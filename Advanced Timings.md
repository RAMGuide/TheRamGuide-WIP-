# Memory Timings



## Important background:

### Prefetch architecture

Many DDR memory systems use prefetching technology to reduce the internal memory clock while still allowing for high transfer rates. The prefetch architecture uses an internal memory bus that is wider than the I/O bus by however many times the prefetch architecture used is. On DDR3 and DDR4 and 8n prefetch architecture is used, this means that internal memory bus is 8 times wider than the external I/O bus. On DDR5 this was increased to 16n due to the technological innovation required in getting DDR5 to the high transfer rates of 6400MT/s that it is specified to run at. This allows DDR4 at 3200MT/s and DDR5 at 6400MT/s to have the same internal core memory clock speed. 

The prefetch architecture works by having the data stored transferred from the internal core memory into prefetch buffers for reads and the data transferred from the prefetch buffers to the internal memory for reads. It takes a single internal memory clock cycle to transfer this data both ways, meaning that when the read command is addressed, after 4 I/O bus clock cycles the data will be in the prefetch buffers, and ready to transfer. Due to this having a CAS latency below 4 on DDR4 is not possible.



## Primary Timings

### tAA (Cas latency, CL)

When the read command is addressed the interal data transfer starts and lasts for a single internal clock cycle

Please do note that in this guide CAS latency will not be called tCL since it is technically a incorrect name for the timing. It will be refrerred to as tAA, CL or simply cas latency in this guide.

![image](https://user-images.githubusercontent.com/77159913/115357843-639f0e00-a200-11eb-9b2f-2cd5dec64df7.png)
Diagram by alatron978#7416 
###### (Yes I made this one, it isn't a jedec diagram)


### tCWL




### tRCD

### tRP

tRP is the delay between when the precharge command is addressed and when the bank(s) are ready for a subsequent activation command. In short this is the delay between closing a row and being able to open a new one.



### tRAS

tRAS is the minimum command period between the activate and precharge commands. In simple terms it is the minimum number of clock cycles between these two commands. This delay is a minimum delay and thus is an 'extension timing' meaning that it extends a command period, and it does not dictate anything directly. An extension timing does not dictate a command period, it just dictates the minimum clock cycles for a command period.
tRAS as a timing has no performance impact when an activate to activate command period is extended by the tRC timing. This concept is later explained in the tRC section as it is crucial to first have an understanding of the tRC timing.


Common myths:
There are many different common myths for a 'minimum' tRAS value or a value to set tRAS to based off other timings, and none of these rules are correct. As mentioned before tRAS is a minimum command period delay, meaning that the ACT to PRE command period can go over this value without a problem, it just cannot take less clocks then tRAS. It is not a fixed value that dictates a fixed time period like many have been led to believe.
Common 'rules' for a minimum tRAS I have heard are the following:

`CL + tRCD = tRAS`

`CL + tRCD + 2 = tRAS`

`CL + tRCD + tRP = tRAS`

`CL + tRCD + tRTP = tRAS`

`tRAS + CL + tRCD = tRAS`

`CL + TRCD + TRRD + TRP = tRAS`

These are just a few examples of the many incorrect rules people have made up, usually from misunderstanding the basics of this timing. The objective fact is every single one of these 'rules' for what you should either set tRAS to or use as a minimum tRAS value are entirely false and hold no truth to them at all.


#### What is the actual minimum value for the tRAS timing?
As tRAS itself is a minimum command period delay, there is no 'minimum' value for tRAS unlike some other timings. If your system allows you to set it to something very low such as 2 or 3 and you do not need a tRAS limit for stability, those values will work just fine. They will not be ignored; those values will be used for tRAS. There is no minimum 'electrical' value like people have been misled to believe, this belief is just false. tRAS is a minimum command period delay, there is no minimum electrical value that this timing must be set above.
However, whilst there is no minimum value for tRAS, there is a point at which lowering tRAS will no longer do anything at all. This is the point where tRAS no longer extends any command delays relative to the actual delays for command periods. The minimum the activate to precharge delay for read operations is:
tRCD + tRTP
The tRCD value used when tRCDWR and tRCDRD timings are independently defined is tRCDRD (This is not a Jedec specification however some platforms have both these timings, such as Ryzen and newer Intel (RKL)).
This can be easily determined from the diagram above where tRCD = activate command to read command delay, and tRTP = read command to precharge command delay. Since tRAS is the minimum activate to precharge delay, if less than or equal to the sum of these values tRAS does nothing for reads. This concept is rather simple, and obvious for why the rules previously defined are incorrect.
Therefore, setting tRAS to or below this value causes tRAS to have absolutely no effect on a memory read operation. However, it can still limit performance under a write operation.

The minimum activate to precharge delay for writing is:
tRCD + tCWL + BC + tWR
The tRCD value used when tRCDWR and tRCDRD timings are independently defined is tRCDWR.
BC on DDR4 is 2 clock cycles, on DDR5 it is 4 clock cycles.

Like the formula for reads can be easily determined from the diagram below where tRCD is the activate command to write command delay, tCWL is the write command to first data delay, BC is the first data to last data clock gap when burst chop is enabled. And finally, tWR is last data to the precharge command.

![image](https://user-images.githubusercontent.com/77159913/115368205-35263080-a20a-11eb-978e-48140129354f.png)
![JESD79-4C P132](https://www.jedec.org/standards-documents/docs/jesd79-4a)


Thus, if tRAS is below or equal to tRCDWR + tCWL + BC + tWR or tRCD + tRTP (whichever is highest) the tRAS timing has absolutely no effect on anything. It does not cause issues, or a performance regression, it simply does nothing at all. Whether you set tRAS to this value or the register minimum value does not matter at all.


#### Why does the write have to include the CAS command and the burst?
The write must include the tCWL timing and the burst due to the prefetch architecture which was explained early. With a read the data is in the memory and gets transferred to the prefetch buffer after 1 physically memory core clock cycle. This means that what ever happens to the data in the physical memory past this point does not matter. The row can be closed without problems as the data is already in the prefetch buffer. Though however with writes the data is being moved into the memory, so the data has to go into the memory before the row can be closed. Thus writing needs extra steps before the row can be closed.

This can be understood when the following diagrams are observed.
![image](https://user-images.githubusercontent.com/77159913/115885599-741ae700-a493-11eb-844c-23050ab34c6d.png)
![image](https://user-images.githubusercontent.com/77159913/115885611-7715d780-a493-11eb-818f-05b8f8ccce23.png)
![Micron GENERAL DDR SDRAM FUNCTIONALITY Technical note P3](https://www.micron.com/-/media/client/global/documents/products/technical-note/dram/tn4605.pdf)





#### Why is tRAS = tCL + tRCD + 2 false and where did the rule come from?
There are many different ways to directly prove that this rule is false. One of which was already mentioned above. This rule doesn't dictate anything, but where did this rule actually come from and how can the original justification be disproven? 
The main place I have seen as a reference for this rule is a post on Overclock.net by Raja@Asus.

I can't find the original post so I'll do this later.

![image](https://user-images.githubusercontent.com/77159913/115372694-81736f80-a20e-11eb-9236-e024f467e650.png)
The image used to substaniate this rule.



### tRC
`It is recommended to read the tRAS section before reading about tRC.`

tRC is the minimum command period between two activate commands and an activate and refresh command for the same bank of memory, this delay like tRAS is a minimum delay and thus it is an 'extension timing'.

#### tRC and tRAS relation. 
tRC and tRAS are two very related timings, and as mentioned in the tRAS section, when tRC extends a command period tRAS is not relevant to performance at all and does nothing. This is shown in the following diagram.

![image](https://user-images.githubusercontent.com/77159913/115889768-94e53b80-a497-11eb-98f8-653d0431e6d6.png)
alatron978#7416

As shown by this diagram, when tRC has an affect tRAS does nothing to the total command period time. And as a tRP always follows a tRAS which goes into the final clocks of the tRC this is always the case. As shown for tRAS to have an affect it must extend past the point where tRC would usually end and allow for another activate. This means that if you are always tRC limited when tRAS limited, setting tRAS from 40 to 21 will do nothing even if tRAS has an effect at 40, but not 21.
Lowering tRAS can in cases allow for a lower tRC to be stable though this is uncommon.
On Intel you do not have to worry about tRC as tRC isn't a timing, and the 'effective' tRC is just the value at which tRC does nothing. 

#### At what value does tRC start to do nothing?
tRC like tRAS has a value at which the timing stops doing anything. This value for tRC is:
tRAS + tRP 
If tRAS is limiting a command period or:
tRCDWR + tCWL + BC + tWR or tRCD + tRTP (highest) + tRP
These formulae may look familiar as they calculate the minimum ACT to PRE command periods for reads and writes assuming that tRAS does not limit these periods. 
These formulae are derived from tRC being the ACT to ACT command period.
Anything below these values causes tRC to do nothing at all. 


## Subtimings 

### tCCD

tCCD is the CAS to CAS command delay for the DRAM. This means it is the gap in clock cycles between two CAS commands being addressed. On DDR4 and DDR5 this timing is spilt into tCCD_S and tCCD_L for the CAS to CAS command delay for a different bank and same bank respectively. This CAS to CAS delay applies to both read to read and write to write scenarios.

These timings are extremely important for memory performance, infact so much that if you raise these timings both from to 4 from 6 on DDR4, you will loose a third of your memory bandwidth which is very impactful. Infact with all other timings equalised, 3200 and 4800 would have almost identical bandwidths if tCCD was 4 for 3200 and 6 for 4800. These timings are very important to watch for when pushing clocks very high, and if you get horrible performance, they are likely to blame.
This of course carries into tRDRD and tWRWR timings when those are preferred.
Reasoning for this:
On DDR4 a burst length of 8 is used and due to the double data rate technology this is 4 I/O bus clock cycles. So a burst lasts for 4 clock cycles, and the gap between two commands to initate a burst being the read or write command is tCCD. Therefore if you have a DDR4 system with tCCD_S and tCCD_L at 6, you will get 2 clock cycles that do nothing after the burst. Meaning that 4 out of 6 clock cycles do something, thus giving you 2 thirds of the original bandwidth. This can also be calculated for other DDR revisions such as DDR5 by using their burst length. E.G, tCCD 10 on DDR5 would be 80% of the original bandwidth due to BL16.
Minimum possible tCCD is BL/2. (BL16 for DDR5 not 32 as dummy reads and writes are used)

DDR5 further spilts into tCCD_L_WR (tCCD_L write, there is no tCCD_S_WR) for standard sticks and the following for 3DS ones;

tCCD_L_slr

tCCD_L_WR_slr

tCCD_L_RTW_slr

tCCD_L_WTR_slr

tCCD_S_slr

tCCD_S_RTW_slr

tCCD_S_WTR_slr

tCCD_S_dlr

tCCD_S_RTW_dlr

tCCD_S_WTR_dlr

With dlr meaning different logical rank, slr meaning same logical rank WTR meaning write to read, and RTW meaning read to write.


As this applies to read to read and write to write scenarios many platforms spilt these timings into tRDRD and tWRWR timings. More detail on these timings below where tertiary timings are explained.

Myths: 
A common myth or these timings is that raising them can help with achieveing higher clock speeds on mainstream DDR4 Intel. However changing tCCD_S and tCCD_L does not do anything if tRDRD_sg, tRDRD_dg, tWRWR_sg or tWRWR_dg are not changed. This timing does not exist to the Intel mainstream IMC although being present in many board bios'. Blame the board manufacters being morons for this.

![image](https://user-images.githubusercontent.com/77159913/114341623-8d6f8980-9b9d-11eb-9596-94d4ee01b230.png)
![JESD79-4C P87](https://www.jedec.org/standards-documents/docs/jesd79-4a)


### tRRD

![image](https://user-images.githubusercontent.com/77159913/114341287-bfccb700-9b9c-11eb-8dee-869dc04d1fb3.png)
![JESD79-4C P88](https://www.jedec.org/standards-documents/docs/jesd79-4a)

### tFAW

tFAW is the 'Four activate window'. This window defines how many clock cycles a window lasts for with every window allowing for 4 activations to occur inside of it. As the gap between activations is tRRD the minimum tFAW can be whilst having a performance impact is tRRD_S * 4 or tRRD_L * 4. tFAW can be set below this but it just won't do anything because at the minimum performance impactful value tFAW is not limiting the activation commands ever. If tRAS is higher then this value it can cause the DRAM to pause and do nothing if 4 consecutive tRRD commands are addressed.

![image](https://user-images.githubusercontent.com/77159913/114340815-bbec6500-9b9b-11eb-9558-12b37ce42b4f.png)
![JESD79-4C P88](https://www.jedec.org/standards-documents/docs/jesd79-4a)
 



t32AW is a timing used by GDDR memory system to define the 32 activate window. This is just like tFAW only 32 activations instead of 4.

### tWTR
![image](https://user-images.githubusercontent.com/77159913/114342058-754c3a00-9b9e-11eb-9a82-ec9ca01f78c7.png)
![JESD79-4C P89](https://www.jedec.org/standards-documents/docs/jesd79-4a)

### tRTP

### tWR

### tREFI

tREFI is the average periodic refresh interval for the DRAM. Meaning on average every tREFI there will be a refresh command addressed. Refresh commands however can be postponed up to 8 times on DDR3 & DDR4 and 4 times on DDR5. These refreshes are postponed, not cancelled. So they will occur eventually and the average time spent refreshing is the same. The time spent refreshing can be calculated by tRFC/tREFI. E.G 400 tRFC and 65535 tREFI, 400/65535 = 0.610360876%

### tRFC

tRFC is the refresh period. Meaning it is the time that the memory takes to refresh in clock cycles. Lower is better for this timing as it reduces the amount of time spent refreshing and maximises useful operational time. This timing can be very performance impactful in situations where tREFI is at Jedec or low such as when using a Ryzen system as Ryzen systems do not allow for tREFI to be modified from Jedec spec. However with a higher tREFI the performance impact is lessened, this is due to the time spent refreshing in % being impactful for performance. With a higher tREFI the reduction in this metric from lets say halving tRFC is lessened.

tREFI increases the DRAM's sensitivity to temperature as the hotter the DRAM is the faster the charge stored in the DRAM's capacitor leaks. tREFI however also reduces power output and thus temperature as the DRAM consumes more power when refreshing then under any other operation. 

tREFI although being a temperature sensitive timing can generally simplely be maxed out under majority of circumstances. 'Maxing out' is setting the timing to the maximum value the platform supports. Whether that be a bios limitation or a CPU register limitation though usually the latter. On most platforms with this timings exposed this value is 65535 for tREFI.

Common myths:
tRFC should be a multiplue of tRC, in most cases 7 or 8. This rule is completely incorrect.

### tCKE

## Tertiary timings

Tertiary timings are platform specific timings that dictate delay between read and write operations. Thus including read to read, read to write, write to read and write to write.

### DDR4 mainsteam Intel




#### tRDRD 
tRDRD on mainstream intel is the read to read branch of tCCD.
With tRDRD_sg being for tCCD_L and tRDRD_dg being for tCCD_S. And then tRDRD_dr and tRDRD_dd for different rank same dimm and different rank different dimm respectivly.
sg meaning same bank group and dg meaning different bankgroup.
As these values are pretty much tCCD for reads and writes they can not be set below 4.
#### tWRWR

tWRWR on mainstream intel is the write to write branch of tCCD.
With tWRWR_sg being for tCCD_L and tWRWR_dg being for tCCD_S. 
sg meaning same bank group and dg meaning different bankgroup.
As these values are pretty much tCCD for reads and writes they can not be set below 4.
#### tRDWR
tRDWR on mainstream intel is a defineable command delay between the read and write commands. As this is a command delay it is not the actual delay between the read and write bursts. The actual delay is what matters for stability and is defined as; 
tCWL-CL+tRDWR = read to write burst delay

Justification:


#### tWRRD





### DDR4 Ryzen AM4

#### tRDRD
tRDRD on AMD is very strange and different to Intel with the timing not directly being tied to tCCD. 
tRDRDSC is the read to read delay for a different bankgroup. 
tRDRDSCL is the read to read delay for the same bankgroup.
tRDRDSD is same dimm different rank.
tRDRDDD is different dimm different rank.

These timings on AMD are very strange, as with tRDRDSC at 1 being full bandwidth it is very clear that this equivlates to tCCD 4. So logic would say that tCCD_S = tRDRDSC + 3. This is further backed up by the data below with tRDRDSC 5 getting around half the bandwidth of tRDRDSC 1, meaning an equivlent tCCD likely of 8.

Meaning these read to read delays are what? Nothing.

![image](https://user-images.githubusercontent.com/77159913/115989534-35576f00-a602-11eb-9b2e-a5b5213a37cd.png)
![image](https://user-images.githubusercontent.com/77159913/115989536-37b9c900-a602-11eb-9e7f-03d850666089.png)
tRDRDSC affect on memory read bandwidth.
Arshia#2457

As can be seen by the above Aida64 read tests with tRDRDSC 1 compared to tRDRDSC 5, bandwidth is essentially halved (Not exactly halved as aida includes ~2~3GB/s of bandwidth as cache, this can be proved with VTune monitoring bandwidth as Aida runs).

#### tRDWR

#### tWRRD

#### tWRWR


### DDR4 Jedec specification

#### tRDWR
The read to write command delay is to be defined as;
CL - CWL + RBL / 2 + 1 tCK + tWPRE for a read to write in the same bankgroup.
CL - CWL + RBL / 2 + 1 tCK + tWPRE for a read to write in a different bankgroup.
tWPRE is the DQS_t, DQS_c differential WRITE Preamble for a 1 tCK premable. This is 1 clock.
RBL is the read burst length.
#### tWRRD
