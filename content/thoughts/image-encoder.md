---
title: "Image Encoders"
date: 2026-03-24
draft: false
---

I've been slowly trying to add more of my photography to this site over the last few weeks. I spent a few hours over the weekend adding images to folders and getting things organized. Most of my photography is digital, with a handful of film scans as well. And they take a variety of sizes and aspect ratios. To keep the hosting costs under control, I figured I would crop and resize the images I was adding so they'd be a more uniform size. And in the process, I went overboard and ended up making them too small to be useful. And they were all renamed by that point.

The solution - Replace them with the originals and start over again. But with 322 compressed and renamed files, and nearly 3,000 originals, there was no practical way to match them by hand.

The solution I landed on was a vision encoder. Specifically, I used [CLIP](https://github.com/mlfoundation/open_clip) to generate a vector for every image in both sets. CLIP is designed to understand images semantically rather than pixel-by-pixel, so a heavily compressed JPEG and its uncompressed original end up very close together in that embedding space, even if one has been scaled down to a tenth of the resolution. Once you have the vectors, finding the best match for any given image is just a dot product — the highest cosine similarity in the target set is almost always the right answer.

I built a workflow with three steps. First, encode everything: load all 322 source images and all 2,897 originals, run them through CLIP in batches on the GPU, normalize the output vectors, and save to disk. That part takes a few minutes and you only have to do it once. Second, match: precompute the full 322×2,897 similarity matrix and build a simple Jupyter interface that shows the top five candidates for each source image as thumbnails alongside their similarity scores and file sizes. Most matches are obvious — scores above 0.97 or so are nearly always correct — so I could auto-accept the confident ones and just click through the edge cases manually. Third, replace: copy each matched original into the art directory on the site, and run it through another (less aggressive) compression pass to keep file sizes reasonable.

The thing I found most interesting about this is how robust CLIP's similarity turned out to be in practice. Images that had been exported for Instagram, watermarked, cropped slightly, or saved at 20% JPEG quality still matched their originals at the top of the list. It's a much more reliable approach than anything you'd get from pixel hashing or histogram comparison, and it requires almost no tuning. If you have any kind of image matching problem where the files don't share metadata, this is worth a shot.
