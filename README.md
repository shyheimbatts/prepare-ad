<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Preparing Active Directory Infrastructure in (Azure)</h1>
This tutorial outlines the implementation of preparing Active Directory Infrastructer in Azure.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Prepare Active Directory Infrastructure in Azure](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022 Datacenter: Azure Edition - x64 Gen2
- Windows 11 Pro (24H2)



<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 Create a Resource Group
- Step 2 Create a Virtual Network and Subnet
- Step 3 Create the Domain Controller Virtual Machine(VM): "DC-1"
- Step 4 Create the Client Virtual Machine(VM): "Client-1"
- Step 5 Set Domain Controller's NIC Private IP Address
- Step 6 Log Into the Domain Controller With Public IP Address & Disable Windows Firewall (Testing Connectivity)

<h2>Deployment and Configuration Steps</h2>

<p>

**Step 1-** Create a Resource Group

<p>
Start by selecting Resource Group↓
</p>
  
</p>



<p>
<img width="1236" height="243" alt="Azure step 1" src="https://github.com/user-attachments/assets/55107137-36f5-4a32-9e96-a0ac20a0c123" />

<p>

**Click Create** to begin the Creation process↓
  
</p>
  
<img width="1432" height="625" alt="Azure step 2" src="https://github.com/user-attachments/assets/61a69690-eaf6-421b-ae65-e32944effcb2" />

<p>

Fill in the basic information needed to create the resource group.

<p>
Start Here↓
</p>

<p>

  **Resource group name** → Active-Directory-Lab
  
</p>

<p>

  **Region** → (US) East US 2
  
</p>

<p>

**Click Review + Create** to confirm the entered information is correct before finalizing the resource group creation.
  
</p>
  
</p>
<img width="878" height="769" alt="Azure step 3" src="https://github.com/user-attachments/assets/8e20a6b0-cc8c-43fb-8067-1247ddb19052" />

<p>

**Click Create** now that all information is confirmed and accurate.
  
</p>
<img width="409" height="761" alt="Azure step 4" src="https://github.com/user-attachments/assets/9cace6d5-84c9-48ff-a7d7-2ea2c739531a" />

<p>

**Step 2-** Create a Virtual Network and Subnet

<p>
  Start by clicking Virtual Networks↓
</p>
  
</p>
<img width="1068" height="178" alt="Azure step 5" src="https://github.com/user-attachments/assets/d1d053fe-e571-440f-909d-4312b6ec34e1" />
<p>

**Click Create** to begin the Creation process↓

</p>
<img width="1199" height="585" alt="Azure step 6" src="https://github.com/user-attachments/assets/97a0e4bc-4171-4067-ae44-eee612dddf0f" />

<p>

Fill in the basic information needed to create the Virtual Network.

<p>
Start Here↓
</p>


**Project Details**

<p>

  **Resource group name** → Active-Directory-Lab
  
</p>

<p>

**Instance Details**

**Virtual network name** → Active-Directory-VNet
  
</p>


<p>

  **Region** → (US) East US 2
  
</p>

<p>

**Click Review + Create** to confirm the entered information is correct before finalizing the Virtual Network.
  
</p>



</p>

<img width="784" height="734" alt="Azure step 7" src="https://github.com/user-attachments/assets/af00e42f-cf39-4ad8-9dbf-3b7c7f3184b3" />

<p>

**Click Create** now that all information is confirmed and accurate.
  
</p>
<img width="554" height="739" alt="Azure step 8" src="https://github.com/user-attachments/assets/518c0e3b-fc73-4082-bfa8-b26afd1ac0c1" />

<p>

**Step 3-** Create the Domain Controller Virtual Machine(VM): "DC-1"

<p>
  Start by clicking Virtual Machines↓
</p>
  
</p>
<img width="1137" height="185" alt="Azure step 9" src="https://github.com/user-attachments/assets/419d8103-6935-4019-8f28-f653a7b48580" />

<p>

**Click Create Virtual Machine** to begin the Creation process↓
  
</p>
<img width="1388" height="568" alt="Azure step 10" src="https://github.com/user-attachments/assets/33b26c97-77b1-44be-9ff3-14dc250f0b69" />

<p>
Fill in the basic information needed to create the Virtual Machine

<p>
Start Here↓
</p>


**Project Details**

<p>

  **Resource group** → Active-Directory-Lab
  
</p>

<p>

**Instance Details**

**Virtual machine name** → dc-1
  
</p>


<p>

  **Region** → (US) East US 2
  
</p>

<p>

**(Continue filling in Virtual Machine Basic Information in Next Picture)**
  
</p>
  
</p>
<img width="864" height="700" alt="Azure step 11" src="https://github.com/user-attachments/assets/4792577b-b137-4835-80ad-6a8b600b279a" />


<p>

**(Continued Basic Information for Virtual Machine from last Picture)**

<p>
 
  **Image** → Windows Server 2022 Datacenter: Azure Edition - x64 Gen2
  
</p>

<p>
  
  **Size** → Standard_D2s_v3 - 2 vcpus, 8 GiB memory
  
</p>

<p>

**Administrator account**

<p>
  
  **Username** → shylabuser
  
</p>

<p>
  
  **Password** → Myworldlab123!
  
</p>

<p>
  
  **Confirm password** → Myworldlab123!
  
</p>
  
</p>
  
</p>
<img width="1075" height="528" alt="Azure step 12" src="https://github.com/user-attachments/assets/362dee79-1a6f-434f-805d-2b63781f9c62" />
<p>

Be sure to Check Mark both boxes for licensing.

<p>

**Then Click Next for Disks↓**
  
</p>
  
</p>
<img width="758" height="554" alt="Azure step 13" src="https://github.com/user-attachments/assets/c45cecef-ea8e-4e22-9713-295a392de2db" />

<p>

**Click Next for Networking↓**


</p>
<img width="439" height="52" alt="Azure step 14" src="https://github.com/user-attachments/assets/51cf9d7f-9d39-444d-9704-b53a9777589b" />
<p>
Fill in the Networking information needed to create the Virtual Machine.

<p>
Start Here↓
</p>

<p>

  **Virtual Network** → Active-Directory-VNet (Active-Directory-Lab)
  
</p>

<p>

  **Subnet** → default
  
</p>

<p>

**Click Review + Create** to confirm the entered information is correct before finalizing the Virtual Machine.

  
</p>
<img width="771" height="618" alt="Azure step 15" src="https://github.com/user-attachments/assets/b827d02b-398e-4f90-96ee-59066bc1d5e4" />

<p>

**Click Create** now that all information is confirmed and accurate.


</p>
<img width="779" height="682" alt="Azure step 16" src="https://github.com/user-attachments/assets/cc9f9e4a-b5ef-469d-9e4e-d270bd6ef5ec" />

<p>

**Step 4-** Create the Client Virtual Machine(VM): "Client-1"
<p>
  Start by clicking Virtual Machines↓
</p>
  
</p>
<img width="1137" height="185" alt="Azure step 9" src="https://github.com/user-attachments/assets/080b898a-8e0c-49f0-a277-0136df1d739f" />

<p>

**Click Create Virtual Machine** to begin the Creation process↓
  
</p>


<img width="1388" height="568" alt="Azure step 10" src="https://github.com/user-attachments/assets/106a269e-08db-42aa-8036-95926e700f8a" />

<p>
<p>
Fill in the basic information needed to create the Virtual Machine

<p>
Start Here↓
</p>


**Project Details**

<p>

  **Resource group** → Active-Directory-Lab
  
</p>

<p>

**Instance Details**

**Virtual machine name** → client-1
  
</p>


<p>

  **Region** → (US) East US 2
  
</p>

<p>

**(Continue filling in Virtual Machine Basic Information in Next Picture)**
  
</p>


  
</p>
<img width="978" height="661" alt="Azure step 17" src="https://github.com/user-attachments/assets/f12a81a6-6f7c-4f76-b154-59bcc5007999" />

<p>
 
  **Image** → Windows 11 Pro, version 24H2 x64 Gen2
  
</p>

<p>
  
  **Size** → Standard_D2s_v3 - 2 vcpus, 8 GiB memory
  
</p>

<p>

**Administrator account**

<p>
  
  **Username** → shylabuser
  
</p>

<p>
  
  **Password** → Myworldlab123!
  
</p>

<p>
  
  **Confirm password** → Myworldlab123!
  
</p>


<img width="812" height="576" alt="Azure step 18" src="https://github.com/user-attachments/assets/b740958d-5771-4d42-9b07-38279eb46c38" />

<p>

Be sure to Check Mark the box for licensing.

</p>

<p>

**Then Click Next for Disks↓**
  
</p>

<img width="485" height="209" alt="Azure step 19" src="https://github.com/user-attachments/assets/a725a78e-c3bf-40af-9859-4f7389ff2ec0" />

<p>

**Click Next for Networking↓**


</p>


<p>
  <img width="439" height="52" alt="Azure step 14" src="https://github.com/user-attachments/assets/fbffcc46-52a3-4983-bc55-bb0a0a7ddfd6" />
 </p>
<p>
Fill in the Networking information needed to create the Virtual Machine.

<p>
Start Here↓
</p>

<p>

  **Virtual Network** → Active-Directory-VNet (Active-Directory-Lab)
  
</p>

<p>

  **Subnet** → default
  
</p>

<p>

**Click Review + Create** to confirm the entered information is correct before finalizing the Virtual Machine.

  
</p>

 
 <img width="937" height="697" alt="Azure step 20" src="https://github.com/user-attachments/assets/f662f356-add2-4287-b8ed-3005d5621e06" />

<p>

**Click Create** now that all information is confirmed and accurate.


</p>
 
 <img width="590" height="682" alt="Azure step 21" src="https://github.com/user-attachments/assets/43dc1e7d-01f2-4c34-a57d-8a808b3229e3" />

<p>

**Step 5-** Set Domain Controller's NIC Private IP Address

Start by clicking Virtual Machines↓

</p>
 
 <img width="1137" height="185" alt="Azure step 9" src="https://github.com/user-attachments/assets/94cde637-6cd7-4e3e-a340-35159ec7fd78" />

 <p>

**Click on DC-1 Virtual Machine↓**
   
 </p>
 <img width="1433" height="288" alt="Azure step 22" src="https://github.com/user-attachments/assets/23dea0e0-6e8b-48da-9b5e-caa1fbec72a9" />
<p>

**Click on Networking drop down and go to Network Settings↓**
  
</p>


<img width="252" height="386" alt="Azure step 23" src="https://github.com/user-attachments/assets/424daa5b-7683-4684-8544-c6bc24f9751d" />

<p>

**Click on the Virtual Network Interface Card(NIC) that DC-1 is using↓**

</p>
  
<p>
  <img width="465" height="104" alt="Azure step 24" src="https://github.com/user-attachments/assets/81be5f42-7338-4110-8b3a-3466ae5450a0" />
 </p>

<p>

**Click on "ipconfig1"↓**
  
</p>
 
<img width="835" height="78" alt="Azure step 25" src="https://github.com/user-attachments/assets/740b5411-ba33-44b8-a21d-becdb765a19b" />

<p>

Under the Private IP address settings, change the allocation from "Dynamic" to "Static" Then Click **Save.**

</p>

<p>

Setting the allocation to "Static" prevents the DC-1 Private IP Address(10.0.0.4) from changing, Regardless of how many times the virtual machine is restarted.
  
</p>

<img width="578" height="484" alt="Azure step 26" src="https://github.com/user-attachments/assets/fae51949-2c79-46da-b672-44c0463d2d87" />

<p>

**Step 6-** Log Into the Domain Controller With Public IP Address & Disable Windows Firewall (Testing Connectivity)

<p>

Start by Clicking Virtual Machines↓

</p>
  
</p>
<img width="1137" height="185" alt="Azure step 9" src="https://github.com/user-attachments/assets/1e7272e2-9c54-4741-8188-82fc1342e327" />

<p>

**Click into DC-1's Virtual Machine to get the Public IP Address↓**
  
</p>
<img width="1433" height="288" alt="Azure step 22" src="https://github.com/user-attachments/assets/fd4f74f0-45ec-49d1-94b7-0c4cfec7ff02" />

<p>

**Copy DC-1's Public IP Address↓**
  
</p>
<img width="511" height="132" alt="Azure step 27" src="https://github.com/user-attachments/assets/3f3e0f04-2dbf-4cbd-83e5-2249556537f7" />

<p>

**Go to Microsoft Remote Desktop Click the "+" sign to Add PC↓**
  
</p>
<img width="820" height="745" alt="Azure step 28" src="https://github.com/user-attachments/assets/70aa15a4-0e69-436a-8996-6fe51b8672a8" />

<p>

**Enter in the Public IP Address → 20.75.54.23 and a Friendly Name - dc 1, Then Click Add.**
  
</p>
<img width="462" height="521" alt="Screenshot 2026-04-10 at 1 09 27 PM" src="https://github.com/user-attachments/assets/5204f44f-b4c6-42fe-a123-1d23439c9663" />

<p>

**Click on DC-1 to Connect to the Virtual Machine.↓**
  
</p>

<p>
 <img width="376" height="224" alt="Screenshot 2026-04-10 at 1 16 57 PM" src="https://github.com/user-attachments/assets/74a82455-9683-461d-a570-f5e9964503d8" />
</p>

<p>

**Enter in User Account Information↓**

<p>
 Username - shylabuser 
</p>

<p>
 Password - Myworldlab123! 
</p>

<p>

**Click Continue to Log In↓**
  
</p>

</p>
<img width="433" height="224" alt="Screenshot 2026-04-10 at 1 17 30 PM" src="https://github.com/user-attachments/assets/4b250d7f-d910-4dcd-8e77-fd8dece2b1f5" />

<p>

**Click Continue↓**
  
</p>

<img width="577" height="151" alt="Screenshot 2026-04-10 at 1 18 35 PM" src="https://github.com/user-attachments/assets/59703e73-35bd-4528-9a19-e3a84b6a14c6" />

<p>
  <img width="257" height="676" alt="Azure step 33" src="https://github.com/user-attachments/assets/91f424a7-0556-4cc4-8656-4ccb1e9b2082" />
  </p>
  <img width="1022" height="798" alt="Azure step 34" src="https://github.com/user-attachments/assets/a0424bd3-6eac-42dc-8700-c7c960047e83" />
<img width="285" height="599" alt="Azure step 35" src="https://github.com/user-attachments/assets/5ace5bb6-6541-4e89-bd54-9f4e83438ac5" />
<p>
  <img width="417" height="228" alt="Azure step 36" src="https://github.com/user-attachments/assets/0ef36eee-da42-4208-8a2b-10e3576fed1f" />
  </p>
  <img width="581" height="425" alt="Azure step 37" src="https://github.com/user-attachments/assets/71043e03-8485-443c-9e60-c99bf0e6a86b" />
  <p>
    <img width="393" height="453" alt="Azure step 38" src="https://github.com/user-attachments/assets/671efa0d-7be3-4371-9bf6-947ff3f03a4e" />
    </p>
    <img width="394" height="449" alt="Azure step 39" src="https://github.com/user-attachments/assets/46cae06d-e36d-491d-b04d-d8694cee2df2" />
    <p>
  <img width="391" height="450" alt="Azure step 40" src="https://github.com/user-attachments/assets/fcb33a6a-1bd8-4fb2-83a9-0c00e800b05e" />
  </p> 
  <img width="1137" height="185" alt="Azure step 9" src="https://github.com/user-attachments/assets/8ca31f7f-8723-4bbd-95e2-c3bb6088139b" />
  <img width="1433" height="288" alt="Azure step 22" src="https://github.com/user-attachments/assets/6aa8f8a6-79e6-425d-94b0-fd88066a600d" />
  <img width="464" height="224" alt="Azure step 41" src="https://github.com/user-attachments/assets/658cc71c-dd00-4d94-bd1b-210192876dbc" />
  <p>
    <img width="269" height="33" alt="Azure step 42" src="https://github.com/user-attachments/assets/91e3a30d-36c5-4213-b53f-89bb3cd54705" />
  </p>
  <img width="247" height="392" alt="Azure step 43" src="https://github.com/user-attachments/assets/1acdc03b-0c46-40f1-899f-ae9199cd6512" />
  <p>
    <img width="464" height="67" alt="Azure step 44" src="https://github.com/user-attachments/assets/2e9cc12b-223f-433a-8060-0538f16d13df" />
  </p>
<img width="286" height="361" alt="Azure step 45" src="https://github.com/user-attachments/assets/1a0e96fc-764d-461e-b1a0-2fe636ec71e4" />
<p>
<img width="324" height="174" alt="Azure step 46" src="https://github.com/user-attachments/assets/62108960-92dc-4b97-b4bb-122d5fd37eb5" />
</p>
<img width="177" height="54" alt="Azure step 47" src="https://github.com/user-attachments/assets/78179522-921c-48c6-9ae2-f70d38477f1d" />
<p>
<img width="459" height="152" alt="Azure step 48" src="https://github.com/user-attachments/assets/84e1d9aa-019a-46ec-839a-a0e3fb8f986d" />
</p>
<img width="1188" height="224" alt="Azure step 49" src="https://github.com/user-attachments/assets/e9fb9167-a654-4aad-bd32-74976720172a" />
<img width="269" height="33" alt="Azure step 42" src="https://github.com/user-attachments/assets/9cfac098-0318-4a0d-a593-44c882abbe7b" />
<p>
<img width="272" height="149" alt="Azure step 50" src="https://github.com/user-attachments/assets/b5165f6c-1533-4d49-8465-92e290e9176a" />
</p>
<img width="822" height="748" alt="Azure step 51" src="https://github.com/user-attachments/assets/ae58c4f8-8b29-4c85-8feb-5de2d1017c06" />
<img width="457" height="530" alt="Azure step 52" src="https://github.com/user-attachments/assets/3fbb10c1-5fe3-426b-b17c-275bb780a4ac" />
<p>
<img width="374" height="216" alt="Azure step 53" src="https://github.com/user-attachments/assets/93a52793-dca7-446d-ba40-c0d1220990dd" />
</p>
<img width="435" height="226" alt="Azure step 54" src="https://github.com/user-attachments/assets/ae1589bb-553f-4f4f-9df2-7d8facabae9a" />
<p>
<img width="565" height="154" alt="Azure step 55" src="https://github.com/user-attachments/assets/7c1df4ba-fad1-49af-8c20-8ce8cb9864a2" />
</p>
<img width="411" height="505" alt="Azure step 56" src="https://github.com/user-attachments/assets/4490e51a-73f4-49c5-b9d7-d8450c3e7741" />
<p>
  <img width="459" height="152" alt="Azure step 48" src="https://github.com/user-attachments/assets/491c1b6e-21cc-44b4-acfd-873c1593d92c" />
</p>
<p>
  <img width="290" height="34" alt="Azure step 57" src="https://github.com/user-attachments/assets/2e5df258-1e2a-4c12-8a45-5e198a8d9689" />
</p>
<img width="376" height="126" alt="Azure step 58" src="https://github.com/user-attachments/assets/38f19968-ef27-4b04-a0fe-95c5eef176e9" />
<p>
<img width="371" height="772" alt="Azure step 59" src="https://github.com/user-attachments/assets/d6c528e1-71d1-41c5-8abc-af567b6b9386" />
</p>
<img width="1114" height="420" alt="Azure step 60" src="https://github.com/user-attachments/assets/4a6a5f49-e0a7-48a9-bd92-c331f3a3bbdb" />
<img width="1101" height="595" alt="Azure step 61" src="https://github.com/user-attachments/assets/8ebe5d04-202a-4fd2-b26d-ad8714263141" />





