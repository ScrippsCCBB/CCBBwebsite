---
title: Aviti Demux Process
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# AVITI Demux

## Sample sheet

Example samplesheet (aviti) available at

[TEMPLATE AVITI
SAMPLESHEET](https://docs.google.com/spreadsheets/d/1K3pzLSfQBB9PhyGJJXdDHNdusKf0h3SjLmu6ItGnEVU/edit#gid=0)

## STEP1

Use the WinSCP or Filezilla to move the samplesheet to the WS in the
directory /ccbbdmxed/ca\_av/fromlims

`cd /ccbbdmxed/ca_av/fromlims` (change directory)

`mv samplesheet.csv  ca_av_0???.samplesheet.csv` (make sure to name the
file with the appropriate run number)

For example for run ca\_av\_0003

`mv samplesheet.csv  ca_av_0003.samplesheet.csv`

Change the permissions of the samplesheet

`chmod 775 ca_av_0???.samplesheet.csv`

Just to be sure, we will change the windows format text file to an unix
format text file,

`/home/ccbbguest/dos2unix ca_av_0003.samplesheet.csv`

## STEP2

The sequencing data for AVITI is mapped to the workstations in the
following location

`/ccbbbcled/aviti/AV233601`

The data should be mapped to this location instead

`/ccbbbcled/aviti/`

So copy the run data to the desired location. Always copy the run data
“NOT ENDING IN PRIME”


    cd /ccbbbcled/aviti/
    rsync -avhP /ccbbbcled/aviti/AV233601/20******_AV233601_ca_av_0****_********_****_**** .

for example for run ca\_av\_0003:


    cd /ccbbbcled/aviti/
    rsync -avhP /ccbbbcled/aviti/AV233601/20231103_AV233601_ca_av_0003_20231103_10X_high .

Check if the folder is copied.

`ls  /ccbbbcled/aviti/20******_AV233601_ca_av_0****_********_****_****`

Once the rync is rename the folder. The current run folder for aviti
contains non standard naming conventions.

`cd /ccbbbcled/aviti/`

`mv 20******_AV233601_ca_av_0****_********_****_**** 20******_AV233601_ca_av_0****`

for example for run ca\_av\_0012:

`mv 20231212_AV233601_ca_av_0012_20231212_mendoza_AM_high 20231212_AV233601_ca_av_0012`

Remove the BCL folder ONLY from the following directory after dispatch

`/ccbbbcled/aviti/`

## STEP 3

### Dual Index Samples

`cd /ccbbdmxed/ca_av`

Run the demux script giving it the run number as parameter

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/1.ccbbdemux_aviti.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/1.ccbbdemux_aviti.sh ca_av_0003`

### Single Index Samples

`cd /ccbbdmxed/ca_av`

Run the demux script giving it the run number as parameter

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/1a.ccbbdemux_aviti_single_index.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/1a.ccbbdemux_aviti_single_index.sh ca_av_0003`

### Dual Index Samples - QC ONLY

Enable QC-only mode, which generates a representative view of run
metrics on one tile and no FASTQ files.

`cd /ccbbdmxed/ca_av`

Run the demux script giving it the run number as parameter

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/2.ccbbdemux_aviti_qc_only.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/2.ccbbdemux_aviti_qc_only.sh ca_av_0003`

### Single Index Samples- QC ONLY

Enable QC-only mode, which generates a representative view of run
metrics on one tile and no FASTQ files.

`cd /ccbbdmxed/ca_av`

Run the demux script giving it the run number as parameter

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/2a.ccbbdemux_aviti_single_index_qc_only.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/2a.ccbbdemux_aviti_single_index_qc_only.sh ca_av_0003`

<!-- # INTERNAL DISPATCH -->

## STEP4

### Dual Index Samples

**Copy the fastqs to FTP for dispatch and generate email for dispatch**

`cd /ccbbdmxed/ca_av`

**Run the following script giving it the run number as parameter**

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/3.ccbbdemux_aviti_results_to_ftp.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/3.ccbbdemux_aviti_results_to_ftp.sh ca_av_0003`

After the successful running of this script the seqdata and QC will be
copied to the

`/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment`

and

`/ccbbftped/PIlastnamelab/arrived/qc/lanecomment_IndexAssignment.csv`

respectively.

The processed data folder will be created in the location:

`/ccbbftped/PIlastnamelab/ftp/processed/lanecomment`

The dispatch emails will also be generated with the ftp links.

<!-- ## STEP4 -->

### Single Index Samples

Copy the fastqs to FTP for dispatch and generate email for dispatch

`cd /ccbbdmxed/ca_av`

Run the following script giving it the run number as parameter

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/3a.ccbbdemux_aviti_single_index_results_to_ftp.sh ca_av_RUN_NUMBER`

for example for run ca\_av\_0003

`/ccbbdmxed/processed/benchmarking/scripts/AVITI_demux_scripts/3a.ccbbdemux_aviti_single_index_results_to_ftp.sh ca_av_0003`

After the successful running of this script the seqdata and QC will be
copied to the

`/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment`

and

`/ccbbftped/PIlastnamelab/arrived/qc/lanecomment_IndexAssignment.csv`

respectively.

The processed data folder will be created in the location:

`/ccbbftped/PIlastnamelab/ftp/processed/lanecomment`

The dispatch emails will also be generated with the ftp links.

Last Updated : January 22, 2024

77

<!-- # 78  -->
<!-- ## STEP 4 -->

Data Distribution - Internal

After the demux is done , the seqdata, QC gets copied to the ftp server
for dispatch.

The seqdata goes to the following location

`/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment`

The QC data goes to the following location

`/ccbbftped/PIlastnamelab/arrived/qc/lanecomment_IndexAssignment.csv`

Once the data is verified - QC is ok ( either passed/missed) , no
barcode clashes etc)

The data needs to be moved to the ftp location for dispatch

SEQDATA


    cd /ccbbftped/PIlastnamelab/ftp/seqdata/
    mv /ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment .

make sure the permissions are set correctly. “others” should have read
and execute permission on the folder and read permissions on the files

If the permissions are not ok use the following to set it

Sets the read and execute permissions for “others” for the seqdata
folder for this dispatch.

`chmod o+rx lanecomment`

`cd lanecomment`

Sets the read permissions for “others” for the all the files in the
seqdata folder for this dispatch.

`chmod o+r *`

Last Updated : January 22, 2024

<!-- 78 -->

79

QC


    cd /ccbbftped/PIlastnamelab/ftp/qc/
    mv /ccbbftped/PIlastnamelab/arrived/qc/lanecomment_IndexAssignment.csv .

make sure the permissions are set correctly. “others” should have read
permissions on the QC file

If the permissions are not ok use the following to set it

`chmod o+r lanecomment_IndexAssignment.csv`

PROCESSED

We usually put a processed folder (even if the lab did not requests
analysis).

The processed folder is created by the script in the following location.

`/ccbbftped/PIlastnamelab/ftp/processed/lanecomment`

## STEP5

Dispatch the data

Use the email template and dispatch the data.

Edit links as needed. Make sure the ftp hyperlinks are functional.

## STEP6

Remove the BCL folder ONLY from the following directory after dispatch

`/ccbbbcled/aviti/`

Data Distribution - Internal

Last Updated : January 22, 2024

80

AVITI

# BCL DATA DISPATCH - Internal

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

## STEP1

Assemble the BCLS in dispatch folder

`cd /ccbbftped/*lab/ftp/bcldata`

Copy the appropriate BCL run folder

`rsync -avhP /ccbbbcled/aviti/20******_AV233601_ca_av_0**** .`

Rename the BCL run folder

`mv 20******_AV233601_ca_av_0**** 20******_AV233601_ca_av_0****.bcls`

Create the tar for the BCL run folder

`tar -zcvf 20******_AV233601_ca_av_0****.bcls.tar 20******_AV233601_ca_av_0****.bcls`

Generate the MD5 for the tarred BCL run folder

`md5sum 20******_AV233601_ca_av_0****.bcls.tar > 20******_AV233601_ca_av_0****.bcls.tar.md5`

Last Updated : December 18, 2023

81

The following applies only to andersenlab runs

## STEP2

Gather data at the external dispatch location on Garibaldi


    login to login03.scripps.edu
    ssh scrippsid@login03.scripps.edu

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

`cd /gpfs/group/andersen/raw_data`

rsync data for dispatch here


    cd /gpfs/group/andersen/raw_data

    rsync -av ccbbguest@ccbbstation04.scripps.edu:/ccbbftped/*lab/ftp/bcldata/20******_AV233601_ca_av_0****.bcls.tar .

    cd /gpfs/group/andersen/raw_data
    rsync -av ccbbguest@ccbbstation04.scripps.edu:/ccbbftped/*lab/ftp/bcldata/20******_AV233601_ca_av_0****.bcls.tar.md5 .

Change the permissions of the copied files.

`chmod 777 20******_AV233601_ca_av_0****.bcls.tar*`

[rsync link](https://www.computerhope.com/unix/rsync.htm)

Last Updated : December 18, 2023

82

# AVITI Data Distribution - External AWS

## Step 1

After the demux is done , the seqdata, QC gets copied to the ftp server
for dispatch.

The seqdata and QC goes to the following location

`/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment`

Once the data is verified - QC is ok

The data needs to be moved to the garibaldi location for dispatch

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

Prepare the seqdata folder before transferring to garibaldi


    cd /ccbbftped/PIlastnamelab/arrived/seqdata/
    mv lanecomment lanecomment.fastqs

    tar -zcvf lanecomment.fastqs.tar lanecomment.fastqs

    md5sum lanecomment.fastqs.tar > lanecomment.fastqs.tar.md5

83

AVITI Data Distribution - External AWS

## STEP2

Gather data at the external dispatch location on Garibaldi


    login to login03.scripps.edu
    ssh scrippsid@login03.scripps.edu

cd to “transit place” where we rsync tar files from Step1 above:

`cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote`

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

`cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote`

rsync data for dispatch here

md5 should be here –&gt;
/mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ tars should be here
–&gt; /mnt/oio/dnaarray/dispatch/disex/*lab/remote/


    cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/
    rsync -av ccbbguest@ccbbstation04.scripps.edu:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar .

    cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/
    rsync -av ccbbguest@ccbbstation04.scripps.edu:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar.md5 .

[rsync site](https://www.computerhope.com/unix/rsync.htm)

84

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE SCREEN SESSION)

## STEP3


    module load dis

    cd /mnt/oio/dnaarray/dispatch/disex/*lab/

disexlist → This command lists the tar and md5 available in the external
customers AWS

disexcopy → This command copies the tar files using config file
remote.conf to the remote location
remote:scrippsresearchngscore-${company}

disexlist | grep ‘lanecomment’ → check if the current dispatch files are
copied

[rclone website](https://rclone.org/)

# BCL Data Backup AVITI

85

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023.

## STEP1

Before running the script,check to see enough space is available for
making tar files

`cd  /ccbbbcled/aviti`

du -sh YYMM\* → To check the space taken by the run folders for Year and
Month du -sh 2309\* → To check the space taken by the run folders for
September 2023 df -h /ccbbbcled → To check how much space is available
in the ccbbbcled location.Check you have enough space before creating
the tar files.

## STEP2

Prepare the BCL TARS for backup.

`cd  /ccbbbcled/aviti/AV233601`

The arguments to the script is YEAR and MONTH.


    /ccbbdmxed/processed/benchmarking/scripts/BCL_backup_scripts/AVITI/1.backup_aviti_bcls_step1_prepare_tars.sh YYYY MM

For example for month of October for the year 2023, use the following

`/ccbbdmxed/processed/benchmarking/scripts/BCL_backup_scripts/AVITI/1.backup_aviti_bcls_step1_prepare_tars.sh202310`

Depending on the number of runs, size of the runs the above script
should take a while to complete.

After the completion of the script, you should see the *.tar and
*.tar.md5 for the all the runs in the specified month and year in this
location

`/ccbbbcled/aviti/dnaarray-bcled-aviti-av233601`

86

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

We will copy the BCL TARS to two locations as a part of the backup
process.

OIO - object storage

TAPE - physical tapes - CCBB will take care of tape backup for now.

## STEP3

Copy the BCL TARS to OIO AND TAPE

`cd /ccbbbcled/aviti/dnaarray-bcled-aviti-av233601`

`/ccbbdmxed/processed/benchmarking/scripts/BCL_backup_scripts/AVITI/2.backup_aviti_bcls_step2_copy_tars_to_OIO.sh`

Depending on the number of runs, size of the runs the above script
should take a while to complete.

## STEP 4

After the copy is done , verify that the bcls are present in the OIO
location.

`module load rclone`

`disoslist | grep “YYYYMM”` → check if the current dispatch files are
copied to the OIO

For example for the October , 2023 data use the following

`disoslist | grep “202310”`

87

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

## STEP5

After successful copy of BCL data to OIO,

Update the BCL backup excel with the relevant details. Please share the
excel sheet with CCBB.

[Example sheet
here](https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0)

## STEP 6

Email [ccbb@scripps.edu](ccbb@scripps.edu) and
[jcducom@scripps.edu](jcducom@scripps.edu) with the list of runs that
were backed up.

After this, the backed up runs will be deleted from FreeNAS by JC.

88

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023.

# DEMUXED Data Backup AVITI

## STEP1

Before running the script,check to see enough space is available for
making tar files

`cd  /ccbbdmxed/ca_av/dispatch`

`du -sh YYYYMM*` → To check the space taken by the run folders for Year
and Month

`du -sh 202310*` → To check the space taken by the run folders for
October 2023

`df -h /ccbbdmxed/` → To check how much space is available in the
ccbbdmxed location.Check you have enough space before creating the tar
files.

\##STEP2

Prepare the DEMUX TARS for backup.

`cd  /ccbbdmxed/ca_av/dispatch`

The arguments to the script is YEAR and MONTH.

`/ccbbdmxed/processed/benchmarking/scripts/DEMUX_backup_scripts/AVITI/1.backup_AVITI_dmxed_step1_prepare_tars.shYYYYMM`

For example for month of september for the year 2023, use the following

`/ccbbdmxed/processed/benchmarking/scripts/DEMUX_backup_scripts/AVITI/1.backup_AVITI_dmxed_step1_prepare_tars.sh202309`

Depending on the number of runs, size of the runs the above script
should take a while to complete.

After the completion of the script, you should see the *.tar and
*.tar.md5 for the all the runs in the specified month and year.

89

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

DEMUXED Data Backup AVITI

We will copy the DEMUX TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

## STEP3

Copy the DEMUXED TARS to OIO AND TAPE

`cd  /ccbbdmxed/ca_av/dnaarray-dmxed-av--0000to0099`

`/ccbbdmxed/processed/benchmarking/scripts/DEMUX_backup_scripts/AVITI/2.backup_aviti_dmxed_step2_copy_tars_to_OIO.sh`

Depending on the number of runs, size of the runs the above script
should take a while to complete.

## STEP 4

After the copy is done , verify that the DEMUXED TARS are present in the
OIO location. module load rclone

`disoslist | grep “YYYYMM”` → check if the current dispatch files are
copied to the OIO

For example for the October , 2023 data use the following

`disoslist | grep “202310”`

90

DEMUXED Data Backup AVITI

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

## STEP 5

After successful copy of DEMUX data to OIO,

Update the excel with the relevant details. Please share the excel sheet
with CCBB.

[Example sheet
here](https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0)

## STEP 6

Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list of
DEMUXED RUNS that were backed up.

After this , the backed up runs will be deleted from FreeNAS by JC.

90
