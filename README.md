# CNC6040 Tool Changer

![Image](https://github.com/Grunwalskii/CNC6040-Automatic-Tool-Changer/blob/main/Pictures/4.jpg)

# CNC6040 Tool Changer Configuration & Setup Guide

## Software & Hardware Integration

### 1. Fusion 360 Tool Change Bypass (Personal/Non-Commercial Tier)
The free personal tier of Autodesk Fusion 360 restricts multi-tool operations by stripping out automatic tool change commands (`M6`) and forcing the generation of separate, individual G-code files for each tool. To bypass this limitation and preserve continuous tool paths in a single output file, you must use a batch post-processing add-in.

* **Bypass Tool:** Download and install the [Fusion360-Batch-Post Add-In by TimPaterson](https://github.com/TimPaterson/Fusion360-Batch-Post).
* **Configuration:** 
  1. Open the **Post Process All** menu inside your Fusion 360 Manufacture workspace.
  2. Locate the patch settings area.
  3. Ensure that the **"Use individual operations"** option is enabled/configured as demonstrated in the system images, which re-links operations across multiple tools into a unified G-code sequence.
  4. Ensure your post-processor settings are matched exactly to your specific machine variant's configuration image.

---

### 2. Mach3 Modern Control Interface
To replace the outdated stock Mach3 user interface with a streamlined, modern layout optimized for rapid setup and clear digital readouts (DRO), this build uses a high-performance custom screen set.

* **Control Interface:** [PA Mach 3 Screen Set by Physics Anonymous](https://www.physanon.com/pa-mach-3-screen-set/).
* **Installation:** Extract the downloaded file structure. Place the custom `.set` file directly inside your root `C:\Mach3\` directory, and copy the accompanying UI asset folders into the `Mach3\Bitmaps\` folder. Load the new interface from the Mach3 upper menu bar under **View -> Load Screens**.

---

### 3. CNC6040 USB Control Board Modifications
To safely automate tool change heights and verify secure tool engagement, the standard CNC6040 USB interface board has been modified to accept two dedicated digital inputs:

* **Electric Touch Probe:** Assigned to a specific digital input pin. This is used for automatic tool height probing.
* **Tool Presence Sensors:** Implemented inside each tool slot/pocket of the rack to detect tool insertion status, instantly halting operations if a tool fails to mount or unmount correctly.
* **Limit Switch Configuration:** To free up and maximize the available input pins on the USB control board for the probe and tool presence sensors, all three physical axis limit switches (X, Y, and Z) have been wired in series to share a single, combined digital input pin.

### 4. Materials & Bill of Materials (BOM)

#### 3D Printed Parts
* **Print Settings:** Print all provided STL files using any standard structural filament (e.g.,PLA, PETG, ABS, or ASA). 
* **Perimeters:** A minimum of **3 wall perimeters**
* **Infill:** A minimum of 20%
  
#### Hardware & Components
To complete the assembly, you will need to source the following off-the-shelf items:

1. **Linear Rods:** 5mm diameter steel rods (Available on [AliExpress](https://de.aliexpress.com/item/4001203233924.html)).
2. **Spring Steel Springs:** 
   * **Wire Diameter:** 0.5 mm
   * **Outer Diameter:** 6.5 mm
   * **Length:** 35 mm
3. Microswitches (Type: HANDLE Available on [AliExpress](https://de.aliexpress.com/item/1005009576690625.html))
4. M6 Screws ~25mm and Nuts
5. Some kind of touchplate (Available on [AliExpress](https://de.aliexpress.com/item/1005008850006833.html)
