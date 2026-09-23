# Ex--3-AWS-Account-setup-and-S3-creation

# Name :SUDEEP RAJ C R
# Reg.no :212224040333

# Introduction

In this experiment, we explored Amazon Web Services (AWS) by creating and managing Amazon Elastic Block Store (EBS) volumes with an Amazon EC2 Linux instance. Amazon EC2 provides scalable virtual servers in the cloud, while Amazon EBS offers persistent block-level storage that can be attached to EC2 instances. The experiment also demonstrated formatting, mounting, storing data, creating snapshots, and restoring volumes from snapshots.

## Objectives

- Launch and verify an Amazon EC2 instance.
- Create an Amazon EBS volume.
- Attach the EBS volume to an EC2 instance.
- Format and mount the EBS volume.
- Store and verify data in the mounted volume.
- Create an EBS snapshot.
- Restore a new volume from the snapshot.

---

## Illustration

### Step 1: Login to AWS Console

Login to the AWS Management Console and open the EC2 Dashboard.

markdown
<img width="1367" height="826" alt="628926137-70b0d7be-7f28-479f-a83d-3ee587c55158" src="https://github.com/user-attachments/assets/54a13288-9230-4495-abab-f8a58899f675" />





---

### Step 2: Open EC2 Dashboard

Navigate to the EC2 Dashboard and verify that the EC2 instance is available.

<img width="1363" height="906" alt="628926217-6ba76379-8c8d-4cf7-a7fe-1cb8a465ee8e" src="https://github.com/user-attachments/assets/ba57e403-6601-4c57-9c21-507d8cf41f1a" />




---

### Step 3: Verify Running EC2 Instance

Open the **Instances** page and ensure that the EC2 instance is in the **Running** state.

<img width="1600" height="905" alt="image" src="https://github.com/user-attachments/assets/2ed85a73-6abc-4e51-a8ca-5f4096e23fe1" />



---

### Step 4: Create an Amazon EBS Volume

Navigate to:

**EC2 → Elastic Block Store → Volumes → Create Volume**

Configure the following:

- Volume Type: General Purpose SSD (gp3)
- Size: 100 GiB
- Availability Zone: Same as the EC2 instance

<img width="1368" height="952" alt="628926350-a21b7fc7-2f41-4e8d-bdf4-9b83155acee8" src="https://github.com/user-attachments/assets/ce5d4cc4-09a2-4c22-a951-f4f6885c6d46" />



---


### Step 5: Add Tags

Provide a name for the volume to make it easy to identify.

Example:

- Key: Name
- Value: My Volume

<img width="1443" height="1090" alt="image" src="https://github.com/user-attachments/assets/83b48331-ed6b-4d52-a7be-107b2402e264" />



---

### Step 6: Attach the Volume

Select the created volume and choose:

**Actions → Attach Volume**

Select the running EC2 instance and specify the device name as:

```
/dev/sdb
```

<img width="1456" height="1080" alt="image" src="https://github.com/user-attachments/assets/f878c990-6018-470d-8815-f724cf06a20f" />




---


### Step 7: Verify Successful Attachment

After attaching the volume, AWS displays a success message.

<img width="1457" height="1080" alt="image" src="https://github.com/user-attachments/assets/fee3bf27-b573-4f4d-ae37-cc10ef99a8a9" />



---

### Step 8: Connect to the EC2 Instance

Select the running instance and click **Connect** using Session Manager.

<img width="1452" height="1083" alt="image" src="https://github.com/user-attachments/assets/3ba6e85e-7e75-4c06-815e-8bad0c5c9160" />



---

### Step 9: Format and Mount the Volume

Run the following Linux commands:

```bash
df -h

sudo mkfs -t ext3 /dev/sdb

sudo mkdir /mnt/data-store

sudo mount /dev/sdb /mnt/data-store

echo "/dev/sdb /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab

cat /etc/fstab

sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"

cat /mnt/data-store/file.txt
```

The commands successfully create the filesystem, mount the EBS volume, and store data.

<img width="1201" height="1309" alt="image" src="https://github.com/user-attachments/assets/5f2042f0-73cd-4d7c-943e-93b36c21dab9" />



---

### Step 10: Create an EBS Snapshot

Navigate to:

**Volumes → Select Volume → Actions → Create Snapshot**

Provide a suitable snapshot name.

<img width="1335" height="1178" alt="image" src="https://github.com/user-attachments/assets/7929aa08-1c8b-481f-8009-622a6162df36" />


---

### Step 11: Verify Snapshot Creation

AWS confirms that the snapshot has been successfully created.

<img width="1457" height="1080" alt="image" src="https://github.com/user-attachments/assets/6cd0dc87-1bb4-44f3-b4a8-6c776b5da8e9" />



---

### Step 12: Verify Stored Data

Confirm that the mounted directory contains the stored data.

```bash
ls /mnt/data-store
```

<img width="1322" height="861" alt="Screenshot 2026-07-30 111007" src="https://github.com/user-attachments/assets/bc8c03c5-2d43-4823-9539-0ba16c73afe9" />



---

### Step 13: View the Snapshot

Navigate to **Elastic Block Store → Snapshots** and verify that the snapshot is available.

<img width="1342" height="1172" alt="image" src="https://github.com/user-attachments/assets/21edb3dd-5c2e-4104-b3a8-c3877afc596a" />


---

### Step 14: Restore Volume from Snapshot

Create a new EBS volume using the previously created snapshot.

Verify that the restored volume appears under **Volumes**.


<img width="1364" height="1153" alt="image" src="https://github.com/user-attachments/assets/2d696eca-bd41-4cb0-b761-ddadc1536d1b" />

<img width="1223" height="1286" alt="image" src="https://github.com/user-attachments/assets/521b6fdd-6c41-478b-8f0b-f221509c5ea6" />

<img width="1338" height="1175" alt="image" src="https://github.com/user-attachments/assets/70863dcb-fd3d-45a6-ae41-119ae65f0277" />


---

## Result

Successfully launched an Amazon EC2 instance, created and attached an Amazon EBS volume, formatted and mounted the storage, stored data on the volume, created an EBS snapshot, and restored a new volume from the snapshot, demonstrating the management of persistent cloud storage in AWS.
