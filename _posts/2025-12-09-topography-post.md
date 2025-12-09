---
layout: post
title: "Topography milling — Cashiers, NC"
date: 2025-12-09 10:00:00 -0500
author: "Coleman Casey"
categories: [projects, posts, cnc, topography]
tags: [topography, bantam, milling, GIS, aspire]
excerpt: >
  How I turned elevation data for Cashiers, NC into a milled wooden topography model — workflow, software, and machine setup.
permalink: /projects/topography-cashiers/
published: true

Short description

I used Vectric Aspire to turn elevation data for Cashiers, NC into a 3D model, adjusted X/Y/Z placement and vertical scale, exported the job for the Bantam, and milled the model out of wood on a Bantam desktop mill. The project emphasized careful axis offsets and conservative toolpaths.
Thorough summary — how I made it


1) Source and prepare elevation data

I began by downloading an area of land for Cashiers, NC and exporting a cropped  heightmap that preserved the ridgelines I wanted to show. That heightmap becomes the single-channel Z source for Aspire.

2) Create and adjust the 3D form in Aspire

I imported the heightmap into Vectric Aspire and used its 3D model tools to convert the image into a relief. In Aspire I adjusted the X/Y placement and the Z scale (vertical exaggeration) so the model read well at the planned physical size. 

3) Aspire and export for Bantam

Within Aspire I exported the toolpaths as G‑code compatible with the Bantam workflow (or exported and imported into Bantam Tools software as needed). I also checked and adjusted X, Y and Z offsets so the physical origin would match the digital job.

4) Milling on the Bantam

On the Bantam I homed axes, set the origin (Z touch‑off or probe), and enabled vacuum. I watched the first minute of machining to confirm tool height and alignment, paused if anything looked off, and let the job run to completion once the initial passes were correct. 




Images:



![Image 1 (IMG_0734)](/assets/images/IMG_0734.jpeg)


![Image 2 (IMG_0735)](/assets/images/IMG_0735.jpeg)








