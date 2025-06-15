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
2. Slice the file using the parameters provided below.  
A key detail is **not to use a longer bottom exposure setting**. Longer exposure on the bottom layers will cause a wider base, which affects fine details on the first layer.  
I use the **same exposure time for the first layer as for all other layers** to maintain consistency and detail accuracy. To get this setting right use a trial-and-error approach. 

    The settings I used work for me but may need to be tuned further for different printers or resins. What I used in this test was:
    - Printer: **Anycubic Photon Mono X 6Ks**
    - Resin: **Phrozen Water-Washable Resin Grey**

#### Slice Parameters

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

---

## Printing and post processing

Once you have the sliced file, you can print the stencil. With exposure times that preserve fine details on the first layer, the print will **not stick to the build plate** and that’s okay! The part is so thin that you can easily peel it off by hand from the bottom of the vat once printing is done. I know it sounds weird and counterintuitive, but it works.

Be prepared for a lot of mess and several failed prints. Let say it’s part of the process.

![Failed attempts](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/PXL_20250601_204526796.jpg)

Once you get a **good** result, clean the part carefully becouse it’s very fragile, especially in areas where components are close together or there are many holes.

Before curing, place the part between two **preheated panes of glass**. This softens the resin during the curing process and helps prevent the stencil from warping. I used a **soldering rework hot plate** to preheat the glass.

![Stencil mid glass](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/PXL_20250601_203711483.jpg)

Curing is the next step that needs to be fine-tuned. I cured my part for **5 minutes** on a spinning table using the **Anycubic Wash & Cure 3.0 Plus**.

The final result is a **flat and detailed stencil** made out of resin.

![Final stencil](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/PXL_20250601_203752330.jpg)

---

## Does it even work?!

The stencil is far from perfect and not quite the same as a laser-cut stainless steel one, but I still gave it a try and the results are shown in the image bellow (more images can be found in the **Images** folder).

![Final result](https://github.com/TilenTinta/Resin_printed_PCB_stencil/blob/main/Images/PXL_20250601_204357867.jpg)


---

## Conclusion

While this method won’t replace professional stainless steel stencils anytime soon, I’m genuinely happy with the results. For a quick and dirty approach, it works surprisingly well — especially when everything is dialed in. Once you’ve fine-tuned your settings the whole process takes no more than **30 minutes** from PCB file to finished stencil.

It’s not perfect, but for hobby projects, rapid prototyping, or testing new board designs without waiting on shipping, this DIY solution gets the job done.
