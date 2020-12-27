# Format a Hard Drive Using the Command Prompt 

## Formatowanie dysku twardego przy wykorzystaniu *wiersza poleceń*

<!-- ...trying to figure out how it is working -->

### STEP 1: Open Command Prompt As Administrator

```bash
search for > cmd
```

run as Administrator

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/asAdmin.jpg" alt="run as administrator">
</p>

or use file explorer and find cmd file, use right mouse button and select *`Run as administrator`*

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/asAdmin2.jpg" alt="run as administrator">
</p>

### STEP 2: Use Diskpart

Once command line is open, type `**diskpart**` and press Enter.

Po włączeniu *wiersza poleceń*, wrowadź komendę `**diskpart**` i zatwierdź klawiszem **Enter**

```bash
c:\windows\system32 > diskpart
```
<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/cmd.jpg" alt="cmd">
</p>


### STEP 3: Type List Disk

The above command will open a Diskpart window. In this window, type `list disk` and press Enter. <br>
It will list all the available drives.


```bash
DISKPART> list disk
```

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/listDisk.png" alt="cmd">
</p>


### STEP 4: Select the Drive to Format

`select disk #` <br>
**`#** *stands for number of disk*


```bash
DISKPART> select disk 2
```

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/select.png" alt="cmd">
</p>


Now type 'select disk (disk number)' as shown above. <br>
Specify the drive number which needs to be formatted.


### STEP 5: Clean the Disk

In this step, type `clean`. This command will permanent delete all files and folders, and successfully clean up the disk.

```bash
DISKPART> clean
```

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/clean.png" alt="cmd">
</p>

### STEP 6: Create Partition Primary

```bash
DISKPART> create partition primary
```

To make the drive again accessible, type `create partition primary`

You can set size of partition with commend:

`create partition primary size=100000`


<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/createPartition.png" alt="cmd">
</p>

```bash
DISKPART> list partition
```

### STEP 7: Format the Drive

```bash
DISKPART> format fs=ntfs quick
```

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/format.png" alt="cmd">
</p>

Now format the drive with FAT or NTFS file system. Type `format fs=ntfs` and press Enter.

If you need to format a hard drive partition to FAT32 or other file systems, replace NTFS with FAT32, exFAT, etc.

**Difference between a "format fs=ntfs" and a "format fs=ntfs quick" **

"When you choose to run a regular format on a volume, files are removed from the volume that you are formatting and the hard disk is scanned for bad sectors. The scan for bad sectors is responsible for the majority of the time that it takes to format a volume.

If you choose the Quick format option, format removes files from the partition, but does not scan the disk for bad sectors. Only use this option if your hard disk has been previously formatted and you are sure that your hard disk is not damaged."


**WARNING**

If you accidentally input format without `fs=ntfs quick or fs=fat32 quick` in DiskPart command prompt, it will execute a full format on your selected hard drive partition.
This command will **erase all saved data** sector by sector. In other words, you'll permanently lose all erased data on the disk with no recovery chance.


### STEP 8: Assign a Drive Letter

```bash
DISKPART> assign
```

To assign a drive letter, you can type 'assign' as shown below.

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/assign.png" alt="cmd">
</p>

You can assign specyfic letter for each volume:

```bash
DISKPART> <br>
list volume <br>
select volume 2 <br>
assign letter=z <br>
```

### STEP 9: List existing volumes

Along with your list of disks, you can also ask Diskpart for a list of detected volumes. <br>
At the **“DISKPART**>” prompt, type list volume:

```bash
DISKPART> list volume
```

<!-- ![preview][test-url] -->


<!-- Linki -->
[test-url]: http://pajlot.pl