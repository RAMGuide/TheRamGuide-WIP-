# Credits
## Guide was made by:

*Arshia*, Tech enthusiast, Arshia#2457 on Discord

*Qubex*, Tech enthusiast, QUBEX#0001 on Discord

*Alatron*, Tech enthusiast, alatron978#7416 on Discord

**This is a guide designed to teach you the basics of DRAM from both theoretical and practical standpoints. In this guide, we aim to cover topics such as the mechanics of DRAM, common implementations of DRAM in computer systems and DRAM overclocking.**

# Table of Contents
1. [What is DRAM](#DRAM)
2. [Why Do We Care](#why-do-we-care)
3. [Types of DRAM](#types-of-dram)
4. [Memory ICs](#memory-ics)
5. [PCB](#pcb)
6. [Brands](#brands)
7. [Memory Timings](#memory-timings)
    1. [Primary Timings](#primary-timings)
    2. [Subtimings](#subtimings)
    3. [Tertiary Timings](#tertiary-timings)
9. [Motherboards and RAM](#motherboards-and-ram)
10. [CPUs and RAM](#cpus-and-ram)
11. [TL:DR](#tldr)
12. [What RAM to buy](#buying-guide)
13. [Chipset/platform Specific Settings and Timings](#platform-guides)

## What Is DRAM


## Why Do We Care
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
