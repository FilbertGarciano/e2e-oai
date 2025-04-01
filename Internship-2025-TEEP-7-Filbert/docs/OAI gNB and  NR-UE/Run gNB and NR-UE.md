## Step 1: Run OAI CN5G
```
cd ~/oai-cn5g
docker-compose up -d
```

## Step 2: Run gNB using RFsimulator
Important notes : You cannot run USRP without the devices. So, just try using the RFsimulator
```
cd ~/openairinterface5g/cmake_targets/ran_build/build
sudo ./nr-softmodem -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb.sa.band78.fr1.106PRB.usrpb210.conf --gNBs.[0].min_rxtxtime 6 --rfsim
```
[Your gNB RFsimulator is running well if it shows like this](https://github.com/user-attachments/assets/71e6ec71-0fa5-4afe-91fd-c1119406a4ff)

## Step 3: Run NR-UE using RFsimulator
In this step, open it using new terminal tab (different from the gNB)
```
cd ~/openairinterface5g/cmake_targets/ran_build/build
sudo ./nr-uesoftmodem -r 106 --numerology 1 --band 78 -C 3619200000 --uicc0.imsi 001010000000001 --rfsim
```
[Your NR-UE RFsimulator is running well if it shows like this](https://github.com/user-attachments/assets/ff12d393-4a7e-4dab-85f1-b0fa42c11b63)

## Step 4: Connection to NG-Core
In this step, open new terminal again (total terminal opened + this: 3 terminals)
```
nano ~/nrue.ulcc.conf
```
After that line, the preview will be like this : [Click this](https://github.com/user-attachments/assets/b3a9c5c4-e31a-435c-bd5e-933443f443a3)
Paste the code below
```
uicc0 = {
  imsi = "001010000000001";
  key = "fec86ba6eb707ed08905757b1bb44b8f";
  opc = "C42449363BBAD02B66D16BC975D77CC1";
  dnn = "oai";
  nssai_sst = 1;
}
```
Exit with Ctrl + X

Continue to end-to-end connectivity test : [Here](
https://github.com/bmw-ece-ntust/internship/blob/2025-TEEP-7-Filbert/docs/RTT%20(Round%20Test%20Trip)/Ping%20Test.md) 

Reference :
https://gitlab.eurecom.fr/oai/openairinterface5g/-/blob/develop/doc/NR_SA_Tutorial_OAI_nrUE.md
