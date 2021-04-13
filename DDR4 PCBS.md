# DDR4 PCB's


## What makes a PCB good and another bad?
A better PCB is one that grants better signal integrity and also shorter trace routing, with the latter usually inducing the former.

Layer counts.

A0 address - "Length to 8th DRAM Compensated" 222.92mm
A2 address - "Length to 8th DRAM Compensated" 244.7991mm
A0 - 
![image](https://user-images.githubusercontent.com/77159913/114537569-b410eb80-9c95-11eb-89d4-28937963172a.png)
A2
![image](https://user-images.githubusercontent.com/77159913/114536732-b45cb700-9c94-11eb-8069-01aeb929b374.png)

## 'a'Rx'b' notation.

The 'a'Rx'b' notation notates the configuration of the dimm. 
The 'a' is the amount of ranks on the stick including physical and logical ranks, more on this later. So if you had 1Rx'b', you would have a single rank stick. Thus 2Rx'b' would be a dual rank stick.
The 'b' is the width of the IC's not to be confused with the count of the IC's. These two get very commonly mixed up. So if you have a 1Rx8 memory stick, this means you have memory chips that are 8 bits wide. Thus with a non-ecc UDIMM, you will have 8 chips. But however if you have a 1Rx16 stick, the chips are 16 bits wide, meaning you only need four to achieve the standard bus width of 64bits for ddr4.

## Physical and logical ranks.

Physical ranks are what most think of when they think of ranks. A logical rank is an array of memory packages that make up the 72/64 bit wide bus. So if you have 16 packages, all 8 bits wide on a non-ecc UDIMM. You would have 2 physical ranks.
Logical ranks are different in that they require multiplue rank packages. If you have 2 logical ranks this means your packages contain two chips, each part of a different rank. This is very common in server memory but is very rare on consumer memory. The only case currently known of logical ranks on consumer UDIMM's is early corsair sticks using 4Gb MMR. 4Gb MMR being two 4Gb MFR chips in a single package. These sticks were single sided dual rank 8GB sticks.
The total ranks that the stick consists of is the product of logical and physical ranks. This is how 8Rx4 sticks are possible with only 36 packages, the packages in this case would have 4 logical ranks.

## Types of PCB's

There are four main types of PCB's, these being, UDIMM's, SODIMM's, RDIMM's and LRDIMM's.
UDIMM's are unbuffered memory dimms in a standard dimm format 


## 'A' UDIMM PCB's

'A' UDIMM pcbs are physically 1Rx8 pcbs. These PCB's are very common for single rank usage with x8 IC's being the most common in single rank consumer sticks.
Almost all single rank consumer sticks are A style PCB's.
These sticks do not include ECC.

As mentioned earlier with the early MMR corsair sticks, these PCB's can be used with dual rank packages thus allowing them to be dual rank sticks by having logical ranks.

A0

The A0 pcbs is the original 1Rx8 non-ecc UDIMM pcb which debuted in 2012 having revisions into 2014. It is designed by spec for 2133 JEDEC operation, though doubling these clocks isn't difficult. This PCB due to its age is very suboptimial in package placement, DQ routing, and pretty much everything else. Due to this PCB's age and sub-optimial design it struggles with clocking past the ~4400~4533. However good A0 pcb's such as the ones used in 4600 cl19 non-rgb G.Skill A0 sticks can achieve ~4700~4800. This pcb whilst struggling with clocks also does not time as well as newer revisions due to it's poor configuration. This PCB at least with Samsung B-Die memory IC's has very intense senstivity to low temperatures, that can start at ~10C.

This PCB in 2021 is no longer produced for performance memory applications by any manufacter, so if you were worried about getting this PCB in a new memory kit do not be worried it isn't produced. This PCB however can catch you out in used memory kits.

Why might you want an A0 PCB?
You might want an A0 PCB if you are using an older platform such as z170, z270 or even z370. These platforms can in cases be optimised for opperation with A0 sticks, and this optimisation can cause them to struggle with running newer A1, A2 or A3 pcb sticks. Making A0 in some cases the better choice.

This PCB is also very commonly confused with the A1 pcb. With somehow this PCB earning it's self the 'A1' name in early day of DDR4 which it is still called by some overclockers today. If you see someone talk about an A1 PCB they are most likely talking about the A0 PCB and just saying the wrong name. 

![image](https://user-images.githubusercontent.com/77159913/114346201-68cbdf80-9ba6-11eb-8985-65841729db4b.png)
![image](https://user-images.githubusercontent.com/77159913/114346554-06271380-9ba7-11eb-8553-1418d17721a4.png)
![image](https://user-images.githubusercontent.com/77159913/114346623-2060f180-9ba7-11eb-9ef1-0caea372a73d.png)
![image](https://user-images.githubusercontent.com/77159913/114346723-44243780-9ba7-11eb-9810-cb6c3050640a.png)

A1

The A1 pcb is the 2nd revision of the A style PCB. This PCB is quite different to other A style PCB's having 9 memory pads, being a 10 layer design and sharing it's design with the D1 ECC PCB. The difference between A1 and D1 is very simple, the PCB is A1 if the 9th memory pad is vacant and D1 if populated. This PCB was designed for 2400 JEDEC operation and is quite a substanital improvement over the original A0 PCB. This PCB due to never being used in performance memory is still quite unknown with clock speed potential. However this PCB has been seen achieving ~5000mt/s.


![image](https://user-images.githubusercontent.com/77159913/114347819-eee92580-9ba8-11eb-819b-9e8b3bceaf14.png)
![image](https://user-images.githubusercontent.com/77159913/114347832-f7416080-9ba8-11eb-974e-571f0dfc2903.png)
![image](https://user-images.githubusercontent.com/77159913/114347842-fb6d7e00-9ba8-11eb-9422-6b0a0ed5b63d.png)
![image](https://user-images.githubusercontent.com/77159913/114347881-0e804e00-9ba9-11eb-9254-4bf328377664.png)
![image](https://user-images.githubusercontent.com/77159913/114349571-7172e480-9bab-11eb-9927-bc3265979ef8.png)

A2

The A2 pcb is the best A style PCB for performance along with being the best clocking DDR4 PCB. A revision of this PCB holds the world record for DDR4 memory frequency currently at 7156.4mt/s. This PCB dropped the 9th pad seen with A1 and moved all of the chips very close to the DQ pins to optimise trace routing. This PCB is used by almost all new 1Rx8 sticks and is the go to choice for overclocking.

![image](https://user-images.githubusercontent.com/77159913/114348234-9a927580-9ba9-11eb-83a7-5192610e537a.png)
![image](https://user-images.githubusercontent.com/77159913/114348209-92d2d100-9ba9-11eb-8b9d-fc38618caee1.png)
![image](https://user-images.githubusercontent.com/77159913/114348177-89e1ff80-9ba9-11eb-815f-24fc93ba1a7d.png)
![image](https://user-images.githubusercontent.com/77159913/114348247-9fefc000-9ba9-11eb-8eba-233aa819d3f6.png)
![image](https://user-images.githubusercontent.com/77159913/114348265-a54d0a80-9ba9-11eb-83c9-48b0d5967556.png)
![image](https://user-images.githubusercontent.com/77159913/114349498-57d19d00-9bab-11eb-9046-9e7b0dbd390e.png)

A3

The A3 PCB is a revision of the A2 pcb which exists to move supported package sizes from 9x13mm (A2) to 10.2x11.0mm (A3). This was done so that wide 16Gb memory IC's are able to fit onto this PCB. This PCB is a very slight regression when compared to A2, but it still clocks extremely well, seen doing 6666mt/s as a max freqency attempt and 6000mt/s stable. 

![image](https://user-images.githubusercontent.com/77159913/114348319-b4cc5380-9ba9-11eb-8971-c74063208030.png)
![image](https://user-images.githubusercontent.com/77159913/114348335-bac23480-9ba9-11eb-993c-fecaaba798fa.png)
![image](https://user-images.githubusercontent.com/77159913/114348353-c0b81580-9ba9-11eb-8d77-a35b5f88b7ab.png)
![image](https://user-images.githubusercontent.com/77159913/114348393-cdd50480-9ba9-11eb-898c-bd166ce77bc1.png)
![image](https://user-images.githubusercontent.com/77159913/114348421-d6c5d600-9ba9-11eb-8c56-737cb77de3c2.png)
![image](https://user-images.githubusercontent.com/77159913/114349162-e4c82680-9baa-11eb-936c-1ed12d917b88.png)


## 'B' UDIMM PCB's

'B' UDIMM pcbs are 2Rx8 UDIMM pcbs. These PCB's are very common for dual rank usage with x8 IC's being the most common in consumer dual rank sticks.
Almost all dual rank consumer sticks are B style PCB's.
These sticks do not include ECC.

B0 

The B0 UDIMM 2Rx8 PCB is a double sided PCB based off the A0 PCB. Like A0 this PCB suffers from poor package placement and most specifically poor DQ routing causing traces to be very long. As this PCB is based off the already quite garbage A0 PCB but it is dual rank, B0 is the worst DDR4 UDIMM non-ecc PCB. This PCB is so bad in fact that over 4000 can be near impossible with this PCB. Much Like A0, B0 is no longer produced for performance memory kits.

31.3mm compenstated length (length from pin to ball)

![image](https://user-images.githubusercontent.com/77159913/114349744-a4b57380-9bab-11eb-9fd7-db31303b91e3.png)
![image](https://user-images.githubusercontent.com/77159913/114349912-d8909900-9bab-11eb-99c4-263850be89ab.png)
![image](https://user-images.githubusercontent.com/77159913/114349943-e3e3c480-9bab-11eb-981d-fa72df5b7c76.png)
![image](https://user-images.githubusercontent.com/77159913/114505882-5ddf8080-9c74-11eb-87ab-2b93f5bbfeaa.png)
![image](https://user-images.githubusercontent.com/77159913/114505894-646df800-9c74-11eb-978d-c123d7648754.png)


B1

As there is no dual sided variant of the A1/D1 pcb B1 is confusingly a double sided 2Rx8 PCB based off the A2 PCB. Like A0 to B0, B1 is a worse PCB then A2 due to the complications of being dual rank. However this PCB is the best 2Rx8 PCB, with variants of this PCB being pushed over 5000mt/s.

16.3mm compenstated length

![image](https://user-images.githubusercontent.com/77159913/114504429-34bdf080-9c72-11eb-822b-7502938afcb4.png)
![image](https://user-images.githubusercontent.com/77159913/114504531-56b77300-9c72-11eb-8d72-6d06630e5b08.png)
![image](https://user-images.githubusercontent.com/77159913/114504538-5b7c2700-9c72-11eb-9541-5a16a74ffdf8.png)
![image](https://user-images.githubusercontent.com/77159913/114504557-62a33500-9c72-11eb-8e60-5c6d22cb2736.png)

B2

The B2 memory PCB is a dual sided 2Rx8 PCB based off the A3 PCB. Like with A2 to A3, B1 to B2 is a regression with the larger pad spacing causing worse routing. This PCB like A3 exists so that wide 16Gb packages can be used, with the maximum package size going from 9x13mm (B1) to 10.2x11mm (B2). This PCB like B1 is quite strong and can achieve 5000mt/s+.

![image](https://user-images.githubusercontent.com/77159913/114504667-92ead380-9c72-11eb-94cd-a65792c7ff78.png)
![image](https://user-images.githubusercontent.com/77159913/114504687-9b430e80-9c72-11eb-8ac4-0592103534b9.png)
![image](https://user-images.githubusercontent.com/77159913/114504710-a26a1c80-9c72-11eb-9eb7-e44b29a71425.png)
![image](https://user-images.githubusercontent.com/77159913/114504768-b746b000-9c72-11eb-8e6d-3408c5dabd32.png)


## 'C' UDIMM PCB's

The C family of UDIMM PCB's consists only of the C0 PCB. The C0 PCB is a 1Rx16 non-ecc pcb. This PCB due to using 16 bit wide chips only has 4 chips. It is decent in clock speed potential with it being shown hitting 4533mt/s. This PCB is used by almost all 2GB DDR4 sticks and very rarely in 4GB sticks, it is a very rare pcb.

C0
![image](https://user-images.githubusercontent.com/77159913/114504916-f1b04d00-9c72-11eb-8956-9c62689d29f6.png)
![image](https://user-images.githubusercontent.com/77159913/114504955-fd037880-9c72-11eb-9945-da07ef8f044d.png)
![image](https://user-images.githubusercontent.com/77159913/114504973-02f95980-9c73-11eb-99f1-644ee63a952e.png)
![image](https://user-images.githubusercontent.com/77159913/114504977-068ce080-9c73-11eb-83db-1974c59871c3.png)
![image](https://user-images.githubusercontent.com/77159913/114505003-11477580-9c73-11eb-87f1-2b8f96819ea1.png)


## 'F' UDIMM PCB's

The F family of UDIMM PCB's consists only of the F0 PCB. F0 PCB is very much essetially a double sided C0 making it a 2Rx16 PCB. This PCB is seen in some early 4GB sticks such as Corsair V4.14 sticks. This PCB like C0 is very rare. Clock speed potential for this PCB is completely unknown however in theorey it should be slightly behind the B1 2Rx8 PCB.

18.74mm max compentsated length

F0
![image](https://user-images.githubusercontent.com/77159913/114505135-45bb3180-9c73-11eb-8ecc-935cb200fcea.png)
![image](https://user-images.githubusercontent.com/77159913/114505170-510e5d00-9c73-11eb-9abe-a02d687372eb.png)
![image](https://user-images.githubusercontent.com/77159913/114505290-7ef3a180-9c73-11eb-965c-4e58bb1bd446.png)



