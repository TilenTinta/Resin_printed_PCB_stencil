# Resin 3D printed PCB stencil

## Introduction

This project explores a fast and DIY-friendly method of creating PCB stencils using a DLP resin 3D printer. The goal was to find out whether it’s possible to print functional stencils for applying solder paste directly onto PCBs—without relying on outsourced laser-cut stainless steel or mylar stencils.

While professionally made stencils are relatively affordable, I wanted to experiment with a self-made alternative that could save both time and cost. Plus, let's be honest—there’s something satisfying about solving hardware problems with a 3D printer and a bit of curiosity.

---

## Preparing files

Once you’ve designed your PCB or even if you’ve already ordered one, open your board file in your PCB design software. In my case, I used KiCad 9.0.

1. In the top menu, click **Plot**,
2. Under **Plot format**, select **DXF**,
3. Choose the layer you want to export. For this stencil, I used the **F.Mask** layer, which represents the front solder mask,
4. Set the units to **millimeters** (or inches, if you absolutely have to), then click **Plot**.

You should now have a file named something like `PCB-F_Mask.dxf` in your selected export folder.

![KiCad settings](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/KiCad_settings.PNG)

Now it's time to create the 3D model for the stencil. I used **Fusion 360 (Hobby Edition)** for this step.

1. Start a new sketch and import your **DXF** file,
2. Draw the outer shape you want around the pads to form the stencil boundary,
3. Extrude the sketch to a thickness of **0.15mm** (or adjust based on your needs).
4. Export the resulting model as an **STL** file to prepare it for slicing and 3D printing.

![Fusion model](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/3D_model_0.15mm.PNG)

---

## Prepare G-code

Import the STL file into your resin printer slicer. In my case, I used **Anycubic Photon Workshop**. This part can be tricky, as the process varies from printer to printer and resin to resin.

1. Lay the model flat on the build plate and **do not** use any supports that lift the model off the surface.
2. Open the resin settings and modify them as needed. The settings I used work for me but may need to be tuned further for different printers or resins.
   - The resin I used was **Phrozen Water-Washable Resin Grey**.

### Slice Parameters

| Parameter                 | Value     |
|---------------------------|-----------|
| Layers Thickness (mm)     | 0.020     |
| Normal Exposure Time (s)  | 2.550     |
| Off Time (s)              | 1.000     |
| Bottom Exposure Time (s)  | 2.500     |
| Bottom Layers             | 1         |
| Anti-alias                | 1         |
| Use Random Erode Shell    | No        |
| Control Type              | Basic     |
| Z Lift Distance (mm)      | 4.000     |
| Z Lift Speed (mm/s)       | 2.000     |
| Z Retract Speed (mm/s)    | 3.000     |



