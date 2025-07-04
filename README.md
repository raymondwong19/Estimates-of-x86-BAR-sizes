# Estimates-of-x86-BAR-sizes
I want to run eGPUs. And I learned my lesson about handling large amounts of VRAM.

If anyone is seeing this, don't take it too seriously. I am only estimating from what worked and what did not. I did learn that maybe I should look for full desktop CPUs the same way I look for full GPU dies for cheap to host my stuff.

JH7110 -> Information on the memory map of this chip is public.
PCIE0 and PCIE1 both have : 256MB of fixed size, start configurable configuration space and 1GB of resizable size address space. For a total of 2.5GB (if most are reallocated to one another or running together). That isn't alot obviously, even GT 730s and R5 340Xs 2GB complain about BAR shortfalls.

Older 2016-2017-2018 low power chips (-T, -U class).
4-8GB. 8GB RTX 2060 SUPER failed on 7600U and 6100T, complaining of memory overlap. 4GB R7 350X works on 6100T. But the 7600U might be able to take a Polaris card with 8GB.
Ultra small chips (even modern (2021)) -> Celeron
6-8GB. Arc A380 6GB works. RTX 2060 SUPER 8GB fails, and that can be because my port's damaged or some other quirk of not being a full desktop implementation.

Modern laptop -> possibly confirmed with eGPU via Thunderbolt or just NVMe.
8-12GB. We all know the Zen 2 5500U took in a RTX 2060 SUPER fine. Tends to bluescreen if it's a AMD GPU however when passed to a VM.

Desktop chip!
Found some cheap 2400GEs. Can take at least 16-24GB of VRAM and be fine. Makes the Intel -T chips look pathetic. A full proper 14600K/9700X desktop seems to be able to take in 3x 16GB cards and still be fine. Forth card and random reboots start to happen if all the card's VRAM are filling up. You'd need to be very darn lucky to have 4 16GB GPUs.
Not so hard for me to have a 16+16+8+8GB quad GPU setup with a 14600K.

Threadripper server/workstation chip!
The latest Threadripper Pro can probably take 200GB of VRAM. They ARE known to work with a pair of 96GB RTX Pro 6000.

IBM POWER10 server chip!
At least 512GB. Those are monsters of expandability. Not available to mere mortals.

Notes : Anyways, you would need Above 4G Decoding to make use of address spaces above 32-bit. Top 32-bit cards tend to have 3GB of VRAM. But as we know, it's hit or miss on Mini PCs or so, vendors mighta have hidden the Above 4G Decoding options in the UEFI.
And anyways, it depends on the graphics card very heavily. There is the legacy function mode for many consumer GPUs, especially older ones, in which they have a 256MB apeture for communication with the main system's PCIe, and the rest of the VRAM is managed internally. And there are some Battlemages and alot of datacenter/Pro cards that require Above 4G Decoding and refuses to work if they are not fully mapped into memory.
