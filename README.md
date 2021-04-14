# Credits
## Guide was made by:

*Arshia*, Tech enthusiast, Arshia#2457 on Discord

*Qubex*, Tech enthusiast, QUBEX#0001 on Discord

*Alatron*, Tech enthusiast, alatron978#7416 on Discord

*Mario*, Tech enthusiast, mario.#9999 on Discord

**This is a guide designed to teach you the basics of DRAM from both theoretical and practical standpoints. In this guide, we aim to cover topics such as the mechanics of DRAM, common implementations of DRAM in computer systems and DRAM overclocking.**

# Table of Contents
1. [What is DRAM](#DRAM)
   1. [Why Do We Care](#why-do-we-care)
2. [Types of DRAM](#types-of-dram)
3. [Memory ICs](#memory-ics)
4. [PCB](#pcb)
5. [Brands](#brands)
6. [Memory Timings](#memory-timings)
    1. [Primary Timings](#primary-timings)
    2. [Subtimings](#subtimings)
    3. [Tertiary Timings](#tertiary-timings)
7. [Motherboards and RAM](#motherboards-and-ram)
8. [CPUs and RAM](#cpus-and-ram)
9. [TL:DR](#tldr)
10. [What RAM to buy](#buying-guide)
11. [Chipset/platform Specific Settings and Timings](#platform-guides)

## What Is DRAM


### Why Do We Care
Optimizing the speed at which the data is written and read and the latency to "trip back" to the CPU largely determines the performance of such DIMMs and whether or not--with the help of assuming other factors like CPU/GPU/monitor resolution/application or gaming/graphical fidelity--we can perceive a difference in the real world.

## Types of DRAM
DRAM is the second fastest form of memory (after SRAM). There are several types of DRAM too (DDR, GDDR, HBM, etc.); however, we're going to focus on the violate state of what most refer to as RAM as in DIMMs. This is a space for us to store data that we cannot handle in L1/L2/L3 cache but still need relatively quicker (slower than that gets kicked to the storages like SSDs and HDD possibly through a pagefile). 

## Memory ICs

## PCBs

## Brands

## Memory Timings

### Primary Timings

### Subtimings

### Tertiary Timings

## Motherboards and RAM
When looking for a motherboard to pair with your RAM, there are multiple things you want to look for. The main things that will affect your motherboards ability to do RAM oc will be the memory topology and the quality of the PCB. When looking at memory topologies (how the traces connected the dimm slots are layed out), you have 3 different option (daisy chain, t-topology and 1DPC (2 dimm motherboards)). 

On modern motherboards (b550, z490 etc) the vast majority of the motherboards will utilise the daisy chain memory topology. Daisy chain topology is when the traces are routed from the cpu socket, to one dimm slot and then to the next (hence the name daisy chain), so that the traces are of uneven length between the 2 dimm slots in the same channel. ![image](https://user-images.githubusercontent.com/82394950/114773832-87b0aa00-9d3d-11eb-8f6e-3961379c200a.png) This generally leads to problems running 4 dimm configurations, due to 2 of the dimm slots having superior signal integrity and OC capabilities compared to the other 2 dimm slots. The ideal configuration for maximum memory frequency atatinable when using a daisy chain board is almost always dimms in slots a2 and b2 (2 and 4).  

Alternatively, some motherboards use t-topology, though these boards aren't nearly as common in comparison to daisychain boards. T-topolgy is when the traces are routed between each dimm then connected to each separately (this explanation sucks), so that each trace connected to dimm is equidistant from the cpu. Because of this, each dimm slot should perform the same, meaning that this topology is ideal for running 4 dimm configurations. THe disadavantge to this memory topology is that it will be inferior to a good daisy chain motherboard for running 2 dimms at high frequency. ![image](https://user-images.githubusercontent.com/82394950/114775979-ef67f480-9d3f-11eb-8264-888824b0d720.png)

Lastly, we have 1DPC/direct topology, or simply put, 2 dimm motherboards. These boards are the absolute best for memory overclocking, because the traces only have to be routed from the cpu socket directly to a single dimm slot, improving the signal integrity and overall memory OC potential of the board. ![image](https://user-images.githubusercontent.com/82394950/114778166-833ac000-9d42-11eb-808c-e3a966bedd99.png) For this reason, high end XOC boards like the z590 tachyon, z590 OC formula, b550 unify-x, z490 aqua (kekkles), use 2 dimm layouts even if it may seem counterintuitive from a non-XOC oriented point of view to pay MORE for LESS maximum ram capacity. ![image](https://user-images.githubusercontent.com/82394950/114777496-c21c4600-9d41-11eb-8c13-7a5056554cb4.png) *z590 Tachyon*

When looking at the memory topology, you also have to take into account that each board manufacturer will implement these basic topologies very differently, and by consequence just because 2 boards use the same memory topology does not mean they will perform even in the same ballpark. For example, a b550 aorus pro will do much better in terms of ram oc than a asus b550-f, even though they are both diasy chain boards, due to gigabytes superior implementation that they have used in their b550 and z490 motherboards. You also have to take into account PCB quality, which will be our next topic.

Motherboard PCB's


## TLDR
Don't buy Corsair

## Buying Guide
When choosing what RAM is right for you, there are a variety of factors to consider. These include your workload, comfortability with RAM overclocking and local market factors. For the sake of this guide, we will only be adressing kits that can be commonly found within the United States in order to be most efficient in our recommendations. Additionally, server-grade RAM, SODIMM and pre-DDR4 ram will be left up to the readers discretion. 

In order to determine what RAM is ideal for your usecase, it is first important to understand how much ram you actually need. On most modern operating systems, this is actually more of an issue than it may sound like at first. These operating systems, from Linux distros to Windows 10 to Windwows XP all tend to overcommit RAM to programs. This means that despite a program only using a set amount of RAM, say 400MB, programs will dynamically allocate more RAM to the program to behave as a buffer. The program may be allocated 1GB on a 32GB system, or 2GB on a 128GB system. This tends to make us believe that we are using more RAM than we actually are. Another common case of this is with video games. In many video games, including the recently released Microsoft FLight Simulator and Cyberpunk 2077 games, RAM usage is often reported as being well above 16GB on 32GB or higher systems. This does not mean that you require 32GB of RAM to run these programs, as running 16GB of total system Ram will lead to this figure being reported as just 10GB of RAM usage by the program. It is merely using more memory if it is available.

One way to circumnavigate this issue is using Process Explorer, a tool bundled within [Microsofts Sysinternals Suite](https://download.sysinternals.com/files/SysinternalsSuite.zip). This useful tool allows you to find how much RAM has been commited to any given program and how much of the RAM is actually being used. In order to determine this, you must click the top set of columns, click "select columns" and then "process memory" and finally check off "WS Private Bytes" and "OK" at the bottom. Upon doing so, Process Explorer should now show this tab, allowing you to find how much RAM is actually being used by a given program. Use this figure in order to determine how much RAM your computer is using. If this value approaches or exceeds 90% of total Physical Memory, it is a sign that you likely do not have enough total system memory and need more RAM for your workload. Using Resource Manager we are able to find the true amount of RAM we require on our computers.

After finding the amount of RAM you require, you must compare this to other parts in your computer. How many memory slots do you have? What memory topology does your motherboard use? Are you planning on upgrading later? What can your CPU's memory controller handle? These are just a few of the important questions that will vary for you. For the bulk of readers, for whom 16GB of RAM should be sufficient, we recommend using a 2x8GB setup. Alternatively, if you are to splurge on 32GB of RAM, it is signficiantly more likely that you will benefit from 2x16GB RAM which, in addition to generally performing better, is also cheaper than comprable 4x8GB setups.

If you are comfortable with the concept of RAM overclocking, we strongly recommend using this guide to determine how you will be overclocking. If chasing the highest amount of performance, RAM using Samsungs 8Gb 'B Die' will be the best choice. For more budget oriented enthusiasts, we recommend Micron 8Gbit 'Rev.E' and 16Gbit 'Rev.B' memory chips, as well as SK Hynix's 8Gbit 'CJR' and 'DJR' solutions. In cases where you are uncertain of what memory chips a kit has, you can refer to the [Memory ICs](#memory-ics) Section of this guide in order to determine what memory chips a kit is using.

Finally, before we give our suggestions of DDR4 UDIMM memory kits, 

## Platform Guides


![image](https://user-images.githubusercontent.com/77159913/114345702-8a789700-9ba5-11eb-8701-2bd3ce015b4e.png)


