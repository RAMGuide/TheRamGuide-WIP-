# DDR4 PCB's

## 'a'Rx'b' notation.

The 'a'Rx'b' notation notates the configuration of the dimm. 
The 'a' is the amount of ranks on the stick including physical and logical ranks, more on this later. So if you had 1Rx'b', you would have a single rank stick. Thus 2Rx'b' would be a dual rank stick.
The 'b' is the width of the IC's not to be confused with the count of the IC's. These two get very commonly mixed up. So if you have a 1Rx8 memory stick, this means you have memory chips that are 8 bits wide. Thus with a non-ecc UDIMM, you will have 8 chips. But however if you have a 1Rx16 stick, the chips are 16 bits wide, meaning you only need four to achieve the standard bus width of 64bits for ddr4.

## Physical and logical ranks.

Physical ranks are what most think of when they think of ranks. A logical rank is an array of memory packages that make up the 72/64 bit wide bus. So if you have 16 packages, all 8 bits wide on a non-ecc UDIMM. You would have 2 physical ranks.
Logical ranks are different in that they require multiplue rank packages. If you have 2 logical ranks this means your packages contain two chips, each part of a different rank. This is very common in server memory but is very rare on consumer memory. The only case currently known of logical ranks on consumer UDIMM's is early corsair sticks using 4Gb MMR. 4Gb MMR being two 4Gb MFR chips in a single package. These sticks were single sided dual rank 8GB sticks.
The total ranks that the stick consists of is the product of logical and physical ranks. This is how 8Rx4 sticks are possible with only 36 chips.



Explain 1Rx8, 2Rx16, etc.

UDIMM - Unbuffered DIMM


## 'A' PCB's

'A' pcbs are 1Rx8 UDIMM non-ecc pcbs. These PCB's are very common for single rank usage with x8 IC's being the most common in consumer sticks.

A0


![image](https://user-images.githubusercontent.com/77159913/114346201-68cbdf80-9ba6-11eb-8985-65841729db4b.png)
![image](https://user-images.githubusercontent.com/77159913/114346554-06271380-9ba7-11eb-8553-1418d17721a4.png)
![image](https://user-images.githubusercontent.com/77159913/114346623-2060f180-9ba7-11eb-9ef1-0caea372a73d.png)
![image](https://user-images.githubusercontent.com/77159913/114346723-44243780-9ba7-11eb-9810-cb6c3050640a.png)

A1

![image](https://user-images.githubusercontent.com/77159913/114347819-eee92580-9ba8-11eb-819b-9e8b3bceaf14.png)
![image](https://user-images.githubusercontent.com/77159913/114347832-f7416080-9ba8-11eb-974e-571f0dfc2903.png)
![image](https://user-images.githubusercontent.com/77159913/114347842-fb6d7e00-9ba8-11eb-9422-6b0a0ed5b63d.png)
![image](https://user-images.githubusercontent.com/77159913/114347881-0e804e00-9ba9-11eb-9254-4bf328377664.png)
![image](https://user-images.githubusercontent.com/77159913/114349571-7172e480-9bab-11eb-9927-bc3265979ef8.png)

A2
![image](https://user-images.githubusercontent.com/77159913/114348234-9a927580-9ba9-11eb-83a7-5192610e537a.png)
![image](https://user-images.githubusercontent.com/77159913/114348209-92d2d100-9ba9-11eb-8b9d-fc38618caee1.png)
![image](https://user-images.githubusercontent.com/77159913/114348177-89e1ff80-9ba9-11eb-815f-24fc93ba1a7d.png)
![image](https://user-images.githubusercontent.com/77159913/114348247-9fefc000-9ba9-11eb-8eba-233aa819d3f6.png)
![image](https://user-images.githubusercontent.com/77159913/114348265-a54d0a80-9ba9-11eb-83c9-48b0d5967556.png)
![image](https://user-images.githubusercontent.com/77159913/114349498-57d19d00-9bab-11eb-9046-9e7b0dbd390e.png)

A3

![image](https://user-images.githubusercontent.com/77159913/114348319-b4cc5380-9ba9-11eb-8971-c74063208030.png)
![image](https://user-images.githubusercontent.com/77159913/114348335-bac23480-9ba9-11eb-993c-fecaaba798fa.png)
![image](https://user-images.githubusercontent.com/77159913/114348353-c0b81580-9ba9-11eb-8d77-a35b5f88b7ab.png)
![image](https://user-images.githubusercontent.com/77159913/114348393-cdd50480-9ba9-11eb-898c-bd166ce77bc1.png)
![image](https://user-images.githubusercontent.com/77159913/114348421-d6c5d600-9ba9-11eb-8c56-737cb77de3c2.png)
![image](https://user-images.githubusercontent.com/77159913/114349162-e4c82680-9baa-11eb-936c-1ed12d917b88.png)




B0 

![image](https://user-images.githubusercontent.com/77159913/114349744-a4b57380-9bab-11eb-9fd7-db31303b91e3.png)
![image](https://user-images.githubusercontent.com/77159913/114349912-d8909900-9bab-11eb-99c4-263850be89ab.png)
![image](https://user-images.githubusercontent.com/77159913/114349943-e3e3c480-9bab-11eb-981d-fa72df5b7c76.png)
![image](https://user-images.githubusercontent.com/77159913/114505882-5ddf8080-9c74-11eb-87ab-2b93f5bbfeaa.png)
![image](https://user-images.githubusercontent.com/77159913/114505894-646df800-9c74-11eb-978d-c123d7648754.png)


B1
![image](https://user-images.githubusercontent.com/77159913/114504429-34bdf080-9c72-11eb-822b-7502938afcb4.png)
![image](https://user-images.githubusercontent.com/77159913/114504531-56b77300-9c72-11eb-8d72-6d06630e5b08.png)
![image](https://user-images.githubusercontent.com/77159913/114504538-5b7c2700-9c72-11eb-9541-5a16a74ffdf8.png)
![image](https://user-images.githubusercontent.com/77159913/114504557-62a33500-9c72-11eb-8e60-5c6d22cb2736.png)

B2
![image](https://user-images.githubusercontent.com/77159913/114504667-92ead380-9c72-11eb-94cd-a65792c7ff78.png)
![image](https://user-images.githubusercontent.com/77159913/114504687-9b430e80-9c72-11eb-8ac4-0592103534b9.png)
![image](https://user-images.githubusercontent.com/77159913/114504710-a26a1c80-9c72-11eb-9eb7-e44b29a71425.png)
![image](https://user-images.githubusercontent.com/77159913/114504768-b746b000-9c72-11eb-8e6d-3408c5dabd32.png)

C0
![image](https://user-images.githubusercontent.com/77159913/114504916-f1b04d00-9c72-11eb-8956-9c62689d29f6.png)
![image](https://user-images.githubusercontent.com/77159913/114504955-fd037880-9c72-11eb-9945-da07ef8f044d.png)
![image](https://user-images.githubusercontent.com/77159913/114504973-02f95980-9c73-11eb-99f1-644ee63a952e.png)
![image](https://user-images.githubusercontent.com/77159913/114504977-068ce080-9c73-11eb-83db-1974c59871c3.png)
![image](https://user-images.githubusercontent.com/77159913/114505003-11477580-9c73-11eb-87f1-2b8f96819ea1.png)

F0
![image](https://user-images.githubusercontent.com/77159913/114505135-45bb3180-9c73-11eb-8ecc-935cb200fcea.png)
![image](https://user-images.githubusercontent.com/77159913/114505170-510e5d00-9c73-11eb-9abe-a02d687372eb.png)
![image](https://user-images.githubusercontent.com/77159913/114505290-7ef3a180-9c73-11eb-965c-4e58bb1bd446.png)



