---
layout: post
title: "SharpImage"
categories:
  - Projects
tags:
  - sharpimage
  - avalonia
  - image
  - codecs
  - csharp
---

[Github page](https://github.com/Echostorm44/SharpImage)

# The Story Behind SharpImage

Every .NET developer who's tried to do serious image processing has probably reached for ImageMagick at some point. I know I did. It's the gold standard for a reason — decades of refinement, support for just about every format under the sun, and it just works. The team behind ImageMagick has done incredible work, and I want to be clear: SharpImage isn't a criticism of what they've built. If anything, this project exists *because* of how much I respect what they created.

So why build it?

I wanted to bring that same capability to .NET — but without the native dependencies. No P/Invoke, no C/C++ bindings, no wrestling with native library distribution across different platforms and architectures. Just a NuGet package that works. Oh, and I was curious whether modern C# could actually compete with C on performance. Turns out, with .NET 10 and a few tricks, it can.

## What It Does

SharpImage is a pure C# reimplementation of an image processing pipeline. Same formats, same operations, same quality but in C#. It started as a personal challenge, got a bit out of hand, and now it's a library, a CLI tool, and there's even a Avalonia-based Photoshop style example application if you want to poke around and see what is possible though I encourage you to make something a little nicer.

## Formats

Supporting 34 image formats covers most of what you'd encounter day-to-day, but I'm particularly happy with the camera raw support — CR2, NEF, ARW, DNG, and 27 other raw formats from various cameras. Proprietary formats are decode-only (because, well, they're proprietary), but DNG supports both read and write. The demosaicing algorithms — Bilinear, VNG, and AHD — handle everything from quick previews to quality-priority processing.

The full list: PNG, JPEG, GIF, BMP, TGA, TIFF, WebP, ICO, AVIF, HEIC, JPEG 2000, JPEG XL, OpenEXR, PSD, DPX, Cineon, HDR, FITS, DICOM, QOI, Farbfeld, WBMP, PNM, PCX, XBM, XPM, DDS, SGI, PIX, SUN, SVG, PDF, and all those camera raw formats.

Beyond formats, there are 40+ colorspaces covered. Not just sRGB — things like Lab, OkLab, Jzazbz, and even HCLp for those who care about perceptually uniform color math.

## Performance

I'll let the numbers do the talking here.

| Operation | Size | Time | Memory |
|-----------|------|------|--------|
| Resize Lanczos3 | 1024→512 | 1.3 ms | 106 KB |
| Resize Lanczos3 (upscale) | 1024→2048 | 4.6 ms | 298 KB |
| GaussianBlur σ=1.0 | 512×512 | 1.4 ms | 10 KB |
| PNG Encode | 512×512 | 7.2 ms | 37 KB |
| PNG Decode | 512×512 | 1.0 ms | 777 KB |
| JPEG Encode Q85 | 512×512 | 10.0 ms | 73 KB |
| JPEG Decode | 512×512 | 9.8 ms | 3.4 MB |
| Raw Demosaic Bilinear | 1024×1024 | 5.2 ms | 644 B |

Benchmarks on .NET 10.0.3 with AVX-512, ShortRun via BenchmarkDotNet. The design is just .NET idioms done intentionally: `Span<T>` instead of array indexing, SIMD intrinsics via `Vector256`/`Vector128`, zero-allocation hot paths with `ArrayPool<T>`, and inner loops that let the JIT remove bounds checks.

## What I Learned

This was my first deep dive into writing performance-sensitive managed code at this scale. Getting to par and past with code written in C required rethinking how you structure pixel loops, how you lay out data in memory, and more than I want to get into here but proving it is possible, that C# isn't the slow little brother anymore felt good.

## Try It

If you want to play with it:

```bash
dotnet add package Echostorm.SharpImage
```

Or clone and build from the [GitHub repo](https://github.com/Echostorm44/SharpImage). There's a CLI with about 228 commands, or use it as a library. The test suite has 1,600+ tests covering formats, colorspaces, transforms, and effects, plus integration tests that compare output against ImageMagick directly if you are curious.
