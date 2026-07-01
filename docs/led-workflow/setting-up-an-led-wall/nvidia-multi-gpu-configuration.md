---
description: Important Settings in the Nvidia Driver
---

# Nvidia Multi-GPU Configuration

Live FX Studio can playout any resolution up to 65k x 65k. However, that realistically is limited by hardware and its drivers. Setting up an Nvidia Mosaic has a resolution limit of 16k x 16k - neither dimension can be exceeded. When setting up large Nvidia Mosaic configurations, multiple GPUs, synced via a Quadro Sync 2 card are necessary. Live FX by default only uses one single GPU for all its processing - the primary GPU of the system. When having multiple GPUs installed, at times the configuration is automatized in the driver, and Live FX might only output white frames through its Dual Head output - whether there's an Nvidia Mosaic configured or not.

The fix for this is to define the OpenGL rendering GPU inside the Nvidia driver, and set it to the primary GPU in the system via the Nvidia Control panel:<br>

<figure><img src="../../assets/image (546).png" alt=""><figcaption><p>Setting the OpenGL rendering GPU to the primary GPU of the system.</p></figcaption></figure>
