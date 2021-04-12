# The Ram Guide
This is a guide designed to teach you the basics of DRAM from both theoretical and practical standpoints. In this guide, we aim to cover topics such as the mechanics of DRAM, common implementations of DRAM in computer systems and DRAM overclocking.


## Memory Timings

## Primary Timings

## tAA (Cas latency)

## tCWL

## tRCD

## tRP

## tRAS

## tRC

## Subtimings 

## tCCD

Comomnly spilt into tRDRD and tWRWR timings.

## tRRD

## tFAW

t32AW

## tWTR

## tRTP

## tWR



## tRFC

tRFC is the refresh period. Meaning it is the time that the memory takes to refresh in clock cycles. Lower is better for this timing as it reduces the amount of time spent refreshing and maximises useful operational time.

## tREFI

tREFI is the average periodic refresh interval for the DRAM. Meaning on average every tREFI there will be a refresh command addressed. Refresh commands however can be postponed up to 8 times on DDR3 & DDR4 and 4 times on DDR5. These refreshes are postponed, not cancelled. So they will occur eventually and the average time spent refreshing is the same. The time spent refreshing can be calculated by tRFC/tREFI. E.G 400 tRFC and 65535 tREFI, 400/65535 = 0.610360876%

## tCKE

# Tertiary timings

Tertiary timings are platform specific timings that dictate delay between read and write operations. Thus including read to read, read to write, write to read and write to write.

# DDR4 mainsteam Intel

tRDRD

tRDWR

tWRRD

