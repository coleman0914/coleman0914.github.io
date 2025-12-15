---
title: "Topography milling — Cashiers, NC"
categories: [projects, posts, cnc, topography]
tags: [topography, bantam, milling, GIS, aspire]



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

What I learned and future plans:

I learned how to turn contour lines and elevation data into a physical model, which made abstract maps feel unexpectedly tangible. Working through mesh creation, texturing, and preparing files for machining taught me practical workflows and the patience that detail work requires. Cutting a quick, low-resolution prototype early saved me from big mistakes — the test piece revealed problems no screen preview showed. If I did this again, I’d make a larger, more dramatic mountain range with finer elevation detail and more varied peaks to better capture the landscape’s character. I’d also set aside extra time for layered materials so the final piece feels more realistic and lived-in.

Project files:

- Download the Coleman Tahoe milling file: [Coleman Tahoe milling CNC](/assets/files/Coleman%20Tahoe%20project%20milling%20(1).cnc)

Workflow: 
Phase 1: Get the Map Data (Terrain2STL)
Select & Adjust: Go to jthatch.com/Terrain2STL/. Drag the red box to your map location.

Exaggerate Height: Use the Vertical Scaling (Z-Scale) slider to make the hills stand out.

Download: Click Generate Model to get the compressed .stl file.

Phase 2: Set Up & Prep (Aspire Vectric 12.5)
Job Setup: Create a new file. Set Job Size (X, Y, Z) to match your physical wood stock. Set Z Zero to the Material Surface.

Import & Size: Go to the Modeling tab and Import the .stl file. Size it to fit your stock (uncheck Lock XYZ ratio).

Refine Component: Access Component Properties (right-click component).

Set Shape Height (e.g., 1.0′′) to control the Z-detail.

Set Base Height (e.g., 0.25′′) to raise the model from the bottom of the stock.

Create Boundary: In the 2D view, draw a Vector Rectangle exactly the size of your stock. This is the final cutout line.

Phase 3: Create the Cut File (Toolpaths)
Always select the Boundary Vector before creating toolpaths.
Home the milling machine- print 
Watch for the first minute to make sure that mill is going smoothly. 

Order	Toolpath	Tool	Purpose
1.	3D Roughing	81′′ End Mill 
2.	3D Finishing	81′′ Ball Nose 
3.	2D Profile	81′′ End Mill 


Issues: In this project I did not run into any issues because of my prior experience using the milling machine during the PCB project. Also, my succesful 3D print of this mountain range gave me confidence going into the milling portion of this. It was a new and intresting project that I have not done before but it was not challenging to me. 

Images:



![Image 1 (IMG_0734)](/assets/images/IMG_0734.jpeg)


![Image 2 (IMG_0735)](/assets/images/IMG_0735.jpeg)








