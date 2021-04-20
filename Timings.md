# Memory Timings

## Primary Timings

### tAA (Cas latency, CL)



Please do note that in this guide Cas latency will not be called tCL since it is technically a incorrect name for the timing. It will be refrerred to as tAA, CL or simply cas latency in this guide.

![image](https://user-images.githubusercontent.com/77159913/115357843-639f0e00-a200-11eb-9b2f-2cd5dec64df7.png)


### tCWL




### tRCD

### tRP

tRP is the delay between when the precharge command is addressed and when the bank(s) are ready for a subsequent activation command. In short this is the delay between closing a row and being able to open a new one.



### tRAS

tRAS is the minimum command delay between the activate and precharge commands


Common myths:
There is are many different common myths for a 'minimum' tRAS value, and none of these rules are right. As mentioned before tRAS is a minimum delay, meaning command periods can go over this value without a problem. It isn't a fixed value that dictates anything like many have been lead to believe.
Common 'rules' for a minimum tRAS I have heard are the following:

CL + tRCD + 2 = 


### tRC

## Subtimings 

### tCCD

tCCD is the CAS to CAS command delay for the DRAM. This means it is the gap in clock cycles between two CAS commands being addressed. On DDR4 and DDR5 this timing is spilt into tCCD_S and tCCD_L for the CAS to CAS command delay for a different bank and same bank respectively. This CAS to CAS delay applies to both read to read and write to write scenarios.

As this applies to read to read and write to write scenarios many platforms spilt these timings into tRDRD and tWRWR timings. More detail on these timings below where tertiary timings are explained.

Myths: 
A common myth or these timings is that raising them can help with achieveing higher clock speeds on mainstream DDR4 Intel. However changing tCCD_S and tCCD_L does not do anything if tRDRD_sg, tRDRD_dg, tWRWR_sg or tWRWR_dg are not changed. This timing does not exist to the Intel mainstream IMC although being present in many board bios'. 

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

### tCKE

## Tertiary timings

Tertiary timings are platform specific timings that dictate delay between read and write operations. Thus including read to read, read to write, write to read and write to write.

# DDR4 mainsteam Intel

tRDRD

tRDWR

tWRRD

tWRWR
