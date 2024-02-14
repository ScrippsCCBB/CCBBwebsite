CCBB DEMUX and LIMS PROCEDURE (July, 2023)

Project 2 Project 4 Project 3 Project 5 Project 1 Project 4 Run 1 Run 2
Run 3 Scenarios & Rules

Single project on single run Multiple projects on single run Single
project on multiple runs

All samples in a project can be either dual indexed or all can be single
index Run can have both “dual index project” and “single index project”

Hashing distance between samples in a run = &gt; 3 Prep types LIMS
<https://genomics-ccbb.scripps.edu/illumina/login.php>

Standard libseq RNASeq Single Cell RNASeq ChIPSeq/Cut&Run Metagenomics
smallRNASeq Variant calling

# Data Storage, Standard, and Distribution

## Data storage

-   NextSeq

-   Novaseq

-   GeoMX

-   AVITI

## Data distribution

-   Internal customers

-   External customers

# Project and Run Naming conventions (as of 2023)

## Internal Project naming conventions (2023)

<figure>
<img src="../docs/assets/images/internal_proj_naming_convention.png"
alt="NF Core Pipeline" />
<figcaption aria-hidden="true">NF Core Pipeline</figcaption>
</figure>

Run type:

Internal Project naming guidelines (2023)

ca\_ns\_teyton\_20230508\_0\_RNAseq\_human\_DC

Fields separated by “\_”

*Field1*: ca

*Field2*: instrument (no, ns, av)

*Field3*: PI’s lastname

*Field4*: Date (multiple dates separate by “-” not “\_“)

*Field5*: 0 usually (if more projects are submitted on the SAME date,
increment it accordingly)

*Field6*: Experimental description (examples: “rnaseq”, “libseq”,
“dnaseq-pool1”, “10X3prime-GEX-CSP-CMO”, “10X5prime-GEX-VDJ”)

*Field7*: species (mouse, rat, human, custom …)

*Field8*: contact person’s initial (2 or 3 letters in CAPS)

## Internal Run Naming Conventions

<figure>
<img src="../docs/assets/images/internal_run_naming_convention.png"
alt="Internal Run Naming Conventions" />
<figcaption aria-hidden="true">Internal Run Naming
Conventions</figcaption>
</figure>

# External Project/Run naming conventions (2023)

<figure>
<img
src="../docs/assets/images/external_proj_or_run_naming_convention.png"
alt="External Run Naming Conventions" />
<figcaption aria-hidden="true">External Run Naming
Conventions</figcaption>
</figure>

<figure>
<img
src="../docs/assets/images/external_proj_or_run_naming_convention_2.png"
alt="External Run Naming Conventions" />
<figcaption aria-hidden="true">External Run Naming
Conventions</figcaption>
</figure>

<figure>
<img src="../docs/assets/images/external_nro_example.png"
alt="External Run Naming Conventions" />
<figcaption aria-hidden="true">External Run Naming
Conventions</figcaption>
</figure>

# Sample Name conventions (2023)

-   No spaces , No underscores

-   Use ALL CAPS

-   In case of multiple projects ,use the prefix “01id” , “02id” , etc
    for samples in each project

-   In case of multiple projects, each sample SHOULD have a unique name
    following the above rules.

-   Use 01idcontactpersoninitials01 etc for sample names. For example ,
    01idXY01, 001XY001 etc

Examples of valid sample names

-   01idYWS01,

-   01idHIPSCMICROGLIA

-   02idHADMSO

Multiple projects submitted from a lab on the SAME DATE and by same
CONTACT PERSON “XY”:

-   01id**PROJECT1XY**01, 02id**PROJECT1XY**02, 03id**PROJECT1XY**03 …

-   01id**PROJECT2XY**01, 02id**PROJECT2XY**02, 03id**PROJECT2XY**03 …

If there are 100 or more samples in a project:

**001**idYWS**001**, **002**idYWS**002**, **003**idYWS**003** …

Checklist

LIMS:

-   Make sure project name follows the naming conventions

-   Run should be connected to ALL projects sequenced in that run - even
    if there is a project whose SampleSheet was generated manually and
    samples not presented on LIMS project page. In these situations
    create a single sample with name “01FAKE” and have a comment saying
    “SampleSheet was generated manually” both on project and run pages.

-   IMPORTANT - every run page at LIMS should have all projects that
    were sequenced in that run AND every project page at LIMS should be
    associated with a run number if sequencing has started or completed!

-   IMPORTANT - each and every sample from various projects in a given
    run should have UNIQUE sample name (sample naming help in provided
    in this PPT file)

-   Each project in a run should have a UNIQUE “Lane Comment” at LIMS

-   If project level and/or sample level read targets are not known set
    them to “0000\_0000” in the Lane Comment at LIMS.

-   Make sure to check that there no gaps in run numbers as you add in
    runs at LIMS. e.g. ca\_ns\_0300 run should be followed by
    ca\_ns\_0301 then ca\_ns\_0302 …

*Login to CCBB Workstation 04*

Username: ccbbguest Password: <P@ss4Guest>!

ssh <ccbbguest@ccbbstation04.scripps.edu>

Linux Basic Commands

<https://hackr.io/blog/linux-cheat-sheet>
<https://bjpcjp.github.io/pdfs/devops/linux-commands-handbook.pdf>

Linux Basic Commands

-   To remove a folder : `rm -rf foldername`

-   To remove a file : `rm filename`

-   To view the manual for a command : `man commandname` , example:
    `man rm`

-   To list the files/folder chronologically : `ls -lth`

# Sample sheet

Example samplesheet (nextseq) available at:

[TEMPLATE\_nextseq2000\_samplesheet.xlsx](https://docs.google.com/spreadsheets/d/1BNk2RSmdWCFSpy8-AL211PjO1lao4yTp/edit#gid=2116979305)

Use the below process to download samplesheet from LIMS Download
samplesheet from LIMS on WS before demux process

`cd /ccbbdmxed/ca_ns/fromlims` (change directory)

`wget --no-check-certificate -O samplesheet.csv 'https://genomics-ccbb.scripps.edu/illumina/service/download_samples.php?run=ca_ns_????_??????_???????-????'`

For example for run ca\_ns\_0302

`wget --no-check-certificate -O samplesheet.csv 'https://genomics-ccbb.scripps.edu/illumina/service/download_samples.php?run=ca_ns_0302_20230710_ELSIEBIO-286_P2'`

the above command should download the sample sheet from LIMS.

Open the samplesheet and inspect it to check the correctness fro lane
comment etc.

`nano samplesheet.csv` (open the samplesheet on command line using nano
editor)

control + X (close the file)

change the name of the downloaded samplesheet.

`mv samplesheet.csv  ca_ns_0???.samplesheet.csv` (make sure to name the
file with the appropriate run number)

For example for run ca\_ns\_0302

`mv samplesheet.csv  ca_ns_0302.samplesheet.csv`

`cd /ccbbdmxed/ca_ns` (change directory)

The BCL data for NextSeq is mapped to the workstations in the following
location

`/ccbbbcled/nextseq2000`

Sequencing for a run is complete if “CopyComplete.txt” is created in the
run folder.

Check if sequencing is complete:

`cd /ccbbbcled/nextseq2000` (change directory to the BCL folder)

`ls` ( list the folders/files)

change directory to the specific run of interest, for example to check
run 302

`cd 230710_VH00464_302_AACJ3MWM5`

`ls -lth` (list the folders ordering them by time)

`/ccbbbcled/nextseq2000/230710_VH00464_302_AACJ3MWM5$ ls -lth`


    total 273K

    -rw-r--r--   1 ilmnuser dnaarray    0 Jul 11 03:01 CopyComplete.txt
    drwxr-xr-x   2 ilmnuser dnaarray    3 Jul 11 03:01 Logs
    drwxr-xr-x   2 ilmnuser dnaarray    3 Jul 11 03:01 PrimaryAnalysisMetrics
    drwxr-xr-x   2 ilmnuser dnaarray  832 Jul 11 03:01 InstrumentAnalyticsLogs
    -rw-r--r--   1 ilmnuser dnaarray  364 Jul 11 03:01 RunCompletionStatus.xml
    drwxr-xr-x   2 ilmnuser dnaarray    4 Jul 11 03:01 Autofocus
    -rw-r--r--   1 ilmnuser dnaarray 2.5K Jul 11 03:01 RunParameters.xml
    drwxr-xr-x 119 ilmnuser dnaarray  141 Jul 11 00:44 InterOp
    -rw-r--r--   1 ilmnuser dnaarray    1 Jul 11 00:44 RTAComplete.txt
    drwxr-xr-x   7 ilmnuser dnaarray    7 Jul 10 21:57 FocusModelGeneration
    drwxr-xr-x   2 ilmnuser dnaarray    3 Jul 10 15:09 WetAutotilt
    drwxr-xr-x   2 ilmnuser dnaarray   15 Jul 10 15:09 Autocenter
    drwxr-xr-x   2 ilmnuser dnaarray    5 Jul 10 11:16 Config
    drwxr-xr-x   2 ilmnuser dnaarray    3 Jul 10 11:16 Recipe
    drwxr-xr-x   3 ilmnuser dnaarray    3 Jul 10 11:16 Data
    -rw-r--r--   1 ilmnuser dnaarray 2.2K Jul 10 11:16 RTA3.cfg
    -rw-r--r--   1 ilmnuser dnaarray 4.0K Jul 10 11:16 RunInfo.xml

## CCBBDEMUX NextSeq

`byobu` (establishes the byobu session where we will do the demux)

F6 ( to detach the session)

byobu-select-session 1 ( to resume the detached session)


    cd /ccbbdmxed/ca_ns

    module load ccbbdemux 
    module load python-addon/3.8.1


    ccbbdemux ca_ns_0302

Once the demux is done, the emails will be generated to the CCBB
mailbox.

The following files/folders are generated for dispatch at
/ccbbftped/PIlastnamelab/arrived:

-   seqdata/lanecomment - contains the fastqs and the md5sum of each of
    the fastq. md5sum is used to verify the data integrity of any file.

-   qc/lanecomment.demux{PASSED/MISSED}.csv - This file lists the QC
    metrics for each of the fastqs for this project and run. The file
    name contains either MISSED/ PASSED. The file is named MISSED if any
    of the fastq misses the read target.

## Folder Structure - NextSeq

<table>
<tbody>
<tr class="odd">
<td>NextSeq Samplesheet</td>
<td></td>
</tr>
<tr class="even">
<td>(LIMS)</td>
<td>/ccbbdmxed/ca_ns/fromlims</td>
</tr>
<tr class="odd">
<td>NextSeq Samplesheet</td>
<td></td>
</tr>
<tr class="even">
<td>(Manual)</td>
<td>/ccbbdmxed/ca_ns/override</td>
</tr>
<tr class="odd">
<td>NextSeq BCL data</td>
<td>/ccbbbcled/nextseq2000</td>
</tr>
<tr class="even">
<td>NextSeq Demux</td>
<td>/ccbbdmxed/ca_ns</td>
</tr>
</tbody>
</table>

    ## ```mermaid
    ## graph TD;
    ##     A-->B;
    ##     A-->C;
    ##     B-->D;
    ##     C-->D;
    ## ```

<figure>
<img src="../docs/assets/images/external_nro_example.png"
alt="Outcome Demux NS Example" />
<figcaption aria-hidden="true">Outcome Demux NS Example</figcaption>
</figure>

<figure>
<img src="../docs/assets/images/ns_process_flowchart.png"
alt="CCBB NextSeq Process FlowChart" />
<figcaption aria-hidden="true">CCBB NextSeq Process
FlowChart</figcaption>
</figure>

## Manual Samplesheet

-   Manual samplesheet is used only when the number of samples are more,
    barcodes not available on LIMS.

-   The i5 should be reverse complemented

*Use the WinSCP or Filezilla to move the samplesheet to the WS in the
directory /ccbbdmxed/ca\_ns/override*

`cd /ccbbdmxed/ca_ns/override (change directory)`

`mv samplesheet.csv  ca_ns_0???.samplesheet.csv` (make sure to name the
file with the appropriate run number)

For example for run ca\_ns\_0306:

`mv samplesheet.csv  ca_ns_0306.samplesheet.csv`

Just to be sure, we will change the windows format text file to an unix
format text file,

`/home/ccbbguest/dos2unix ca_ns_0306.samplesheet.csv`

Change the permissions of the samplesheet

`chmod 664 ca_ns_0???.samplesheet.csv`

Check if run is complete : `/ccbbbcled/nextseq2000`

byobu-select-session 1 ( to resume the detached session)

Once run is complete, proceed with demux.

`cd /ccbbdmxed/ca_ns` (change directory)

Load the required modules

    module load ccbbdemux 
    module load python-addon/3.8.1

Check if the modules are loaded

`module list`

`ccbbdemux ca_ns_0306`

## Top Unknown barcodes

If any sample did not get any reads, or very few reads ( ~100s , ~ 1ks)
, we would need to verify the top unknown barcodes

`cd /ccbbdmxed/ca_ns/20??????_VH00464_0???_?????????/`

Run the following script if the run has dual index barcodes

`/home/ccbbguest/nextseq_top_unknown_dual_index_barcode.sh`

Once the script completes, check the outputs. You should see 2 files,
*laneBarcode\_dual\_index.html* and *top\_unknown\_dual\_index.txt*

`ls`

`cat top_unknown_dual_index.txt`

Run the following script if the run has single index barcodes

`/home/ccbbguest/nextseq_top_unknown_single_index_barcode.sh`

Once the script completes, check the outputs. You should see 2 files,
*laneBarcode\_single\_index.html* and *top\_unknown\_single\_index.txt*

`ls`

`cat top_unknown_single_index.txt`

**NOTE: If a run has a mix of single and dual index barcodes, then run
both the scripts one after the other. 23**

[Reverse complement
Tool](https://arep.med.harvard.edu/labgc/adnan/projects/Utilities/revcomp.html)
[Hamming Distance
Tool](http://valjok.blogspot.com/2015/08/hamming-distance-online.html)

## BYOBU

F2 - New Tab F3 - Navigate to the previous tab F4 - Navigate to the next
tab F8 - Rename a Tab F7 - Enter scrollback F6 - Detach from a byobu
session [BYOBU
Cheatsheet](https://cheatography.com/mikemikk/cheat-sheets/byobu-keybindings/)

## Scenario 1 - Barcode Collision

**Barcodes should always have the hamming distance of 3 between them.**

For example, for run ca\_ns\_0315 the following 2 samples

01idS021,01idS021,,,,**AGTAGGCT**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,
02idS031,02idS031,,,,**AGGCGAGA**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,

i7s , i5s are changed to be identical

01idS021,01idS021,,,,**AGTAGGCT**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,
02idS031,02idS031,,,,**AGTAGGCT**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,

In case of above scenario we cannot demux samples 01idS021 and 02idS031.
Remove the two samples from the samplesheet and then proceed with
regular demux.


    module load ccbbdemux 
    module load python-addon/3.8.1

    module list  

    ccbbdemux ca_ns_0315

## Scenario 2 - Hamming Distance 1

Barcodes should always have the hamming distance of 3 between them. For
example, for run ca\_ns\_0315 the following 2 samples

01idS021,01idS021,,,,**AGTAGGCT**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,
02idS031,02idS031,,,,**AGGCGAGA**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,

i7s differ by 1 base only (instead of the recommended 3 mismatches), i5s
are the same

01idS021,01idS021,,,,**AGTAGGCT**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,
02idS031,02idS031,,,,**AG***TA***GGCA**,GGTTCAGG,ca\_ns\_0315\_02\_0000\_0000\_williamson\_01\_LS-S00-01-NR0,

In case of above scenario we use exact match to demux.

    module load ccbbdemux 
    module load python-addon/3.8.1

    module list  

    ccbbdemuxbarcodemismatcheszero ca_ns_0315

To get the number of reads in a fastq file

`echo $(zcat name.fastq.gz|wc -l)/4|bc`

Script to get the number of reads for all the fastq files in a
particular directory

`/home/ccbbguest/count_fastq_reads.job`

## Data Distribution - Internal

After the demux is done, the seqdata, QC gets copied to the ftp server
for dispatch.

The seqdata goes to the following location

`/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment`

The QC data goes to the following location

`/ccbbftped/PIlastnamelab/arrived/qc/lanecomment`

Once the data is verified - QC is ok ( either passed/missed) , no
barcode clashes etc) The data needs to be moved to the ftp location for
dispatch

SEQDATA

`cd /ccbbftped/PIlastnamelab/ftp/seqdata/`
`mv /ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment .`

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

### QC

`cd /ccbbftped/PIlastnamelab/ftp/qc/`

`mv /ccbbftped/PIlastnamelab/arrived/qc/lanecomment.demux{PASSED/MISSED}.csv .`

make sure the permissions are set correctly. “others” should have read
permissions on the QC file If the permissions are not ok use the
following to set it

`chmod o+r lanecomment.demux{PASSED/MISSED}.csv`

PROCESSED

We usually put a processed folder(even if the lab did not requests
analysis).


    cd /ccbbftped/PIlastnamelab/ftp/processed/
    mkdir lanecomment

Sets the read and execute permissions for “others” for the processed
folder for this dispatch.

`chmod o+rx lanecomment`

`cd lanecomment` `cp ../contact_ccbb@scripps.edu_for_analysis .`
`chmod o+r *`

# NextSeq Non 10X

## BCL DATA DISPATCH - Internal

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP1

Assemble the BCLS in dispatch folder

`cd /ccbbftped/*lab/ftp/bcldata/`

Copy the appropriate BCL run folder

`rsync -avhP /ccbbbcled/nextseq2000/2*****_VH00464_***_******** .`

Rename the BCL run folder

`mv 2*****_VH00464_***_******** 2*****_VH00464_***_********.bcls`

Create the tar for the BCL run folder

`tar -zcvf 2*****_VH00464_***_********.bcls.tar 2*****_VH00464_***_********.bcls`

Generate the MD5 for the tarred BCL run folder

`md5sum 2*****_VH00464_***_********.bcls.tar > 2*****_VH00464_***_********.bcls.tar.md5`

STEP2

Gather data at the external dispatch location on Garibaldi

login to login03.scripps.edu

`ssh scrippsid@login03.scripps.edu`

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /gpfs/group/andersen/raw\_data

rsync data for dispatch here cd /gpfs/group/jin/Sequencing/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/2*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar
.

cd /gpfs/group/jin/Sequencing/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/2*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5
.

Change the permissions of the copied files. chmod 777
2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar\*

<https://www.computerhope.com/unix/rsync.htm>

Novaseq BCL DATA DISPATCH - Internal The following applies only to Xin
jin lab runs 30

Hi XXXX, This is related to your sequencing project - run -

Internal Data Dispatch:

Raw BCL data has been uploaded to the following location on Garibaldi:
/gpfs/group/jin/Sequencing/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar

md5sum:
/gpfs/group/jin/Sequencing/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5

Please confirm that you have access to this data.

Novaseq BCL DATA DISPATCH - Internal The following applies only to Xin
jin lab runs 31

NextSeq BCL DATA DISPATCH - Internal

TEMPLATE EMAIL (INTERNAL) This is related to your sequencing project –
run –

Internal Data Dispatch:

Instructions to access the data dispatched:
<https://github.com/ScrippsCCBB/CCBBwebsite/blob/main/FileZilla_Instructions_CCBB.pdf>

Please download your sequencing data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/seqdata/lanecomment.bcls/>
32

Data Distribution - External AWS After the demux is done , the seqdata,
QC gets copied to the ftp server for dispatch.

The seqdata goes to the following location
/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment

The QC data goes to the following location
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment

Once the data is verified - QC is ok ( either passed/missed) , no
barcode clashes etc) The data needs to be moved to the garibaldi
location for dispatch (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
BYOBU SESSION)

STEP1 Prepare the seqdata folder before transferring to garibaldi cd
/ccbbftped/PIlastnamelab/arrived/seqdata/

mv lanecomment lanecomment.fastqs

tar -zcvf lanecomment.fastqs.tar lanecomment.fastqs

md5sum lanecomment.fastqs.tar &gt; lanecomment.fastqs.tar.md5

33

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

cd to “transit place” where we rsync tar files from Step1 above:

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

rsync data for dispatch here md5 should be here –&gt;
/mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ tars should be here
–&gt; /mnt/oio/dnaarray/dispatch/disex/*lab/remote/

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar
.

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar.md5
.

<https://www.computerhope.com/unix/rsync.htm>

Data Distribution - External AWS 34

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE SCREEN SESSION)

STEP3 module load dis

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/

disexlist → This command lists the tar and md5 available in the external
customers AWS

disexcopy → This command copies the tar files using config file
remote.conf to the remote location
remote:scrippsresearchngscore-${company}

disexlist | grep ‘lanecomment’ → check if the current dispatch files are
copied

<https://rclone.org/>

Data Distribution - External AWS 35

NextSeq 10X MULTIOME

Example samplesheet (10X nextseq) available at
TEMPLATE\_nextseq2000\_10X\_samplesheet

Lane comment :
ca\_ns\_0???\_0?\_0000\_0000\_PIlastname\_01\_SC-MUL-01-HU0

Sample Names No spaces , No underscores Use ALL CAPS Use the prefix
“01id” , “02id” , etc for each sample Give meaningful sample names

Check if the NextSeq run is complete : Refer slide 15

If all the above steps are done , proceed to the demux

Single cell Type of SC exp MUL– Multiome 5PR - 5 PRIME 3PR - 3 PRIME
Species HU0 - Human MM0 - Mouse

36

NextSeq 10X MULTIOME

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP1 Create the directory for demux cd /ccbbdmxed/ca\_ns mkdir
lanecomment for example : mkdir
ca\_ns\_0318\_01\_0000\_0000\_lotz\_01\_SC-MUL-01-HU0

Change the permissions of the folder chmod 774 lanecomment cd
lanecomment

STEP2 create/ copy the samplesheet to the demux directory cd lanecomment

Use the WinSCP or Filezilla to move the samplesheet to the WS. The
samplesheet must be named csv.csv Just to be sure, we will change the
windows format text file to an unix format text file,
/home/ccbbguest/dos2unix csv.csv

Change the permissions of the samplesheet chmod 774 csv.csv

37

NextSeq 10X MULTIOME

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP3 Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/MULTIOME\_scripts/1.cellranger-arc\_mkfastq\_nextseq.sh
RUN\_NUMBER

for example for run 318
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/MULTIOME\_scripts/1.cellranger-arc\_mkfastq\_nextseq.sh
318

Once the demux is done the fastqs will be generated in the following
folder /ccbbdmxed/ca\_ns/lanecomment/OUTS/outs/fastq\_path/A*/*/\*gz

38

NextSeq 10X MULTIOME

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP4
Assemble the fastqs in a folder /ccbbdmxed/ca\_ns/lanecomment/
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/MULTIOME\_scripts/2.results\_fastqs.sh

After the execution of the above script you should see the following
folder with the fastqs and the md5 file

/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs

STEP5 Move the fastqs folder to the ftp location for dispatch (INTERNAL)
cd /ccbbftped/PIlastnamelab/ftp/seqdata/ rsync -avhP
/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs .

make sure the permissions are set correctly. “others” should have read
and execute permission on the folder and read permissions on the files
If the permissions are not ok use the following to set it

chmod o+rx lanecomment.tenxfastqs

cd lanecomment.tenxfastqs

chmod o+r \*

Sets the read and execute permissions for “others” for the 10X seqdata
folder for this dispatch. Sets the read permissions for “others” for the
all the files in the 10X seqdata folder for this dispatch. 39

PROCESSED We usually put a processed folder(even if the lab did not
requests analysis).

cd /ccbbftped/PIlastnamelab/ftp/processed/ mkdir lanecomment chmod o+rx
lanecomment

cd lanecomment cp ../<contact_ccbb@scripps.edu>\_for\_analysis . chmod
o+r \*

NextSeq 10X MULTIOME

Sets the read and execute permissions for “others” for the processed
folder for this dispatch. 40

NextSeq 10X MULTIOME

TEMPLATE EMAIL (INTERNAL) This is related to your sequencing project –
run –

Internal Data Dispatch:

Instructions to access the data dispatched:
<https://github.com/ScrippsCCBB/CCBBwebsite/blob/main/FileZilla_Instructions_CCBB.pdf>

Please download your processed data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/processed/lanecomment/>

Please download your sequencing data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/seqdata/lanecomment.tenxfastqs/>
41

NextSeq 10X 5PR , 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP1 Create the directory for demux cd /ccbbdmxed/ca\_ns mkdir
lanecomment for example : mkdir
ca\_ns\_0103\_0?*0000\_0000\_lotz\_01*??-??-01-??

Change the permissions of the folder chmod 774 lanecomment cd
lanecomment

STEP2 create/ copy the samplesheet to the demux directory cd lanecomment

Use the WinSCP or Filezilla to move the samplesheet to the WS.

The samplesheet must be named csv.csv Just to be sure, we will change
the windows format text file to an unix format text file,
/home/ccbbguest/dos2unix csv.csv

Change the permissions of the samplesheet chmod 774 csv.csv

42

NextSeq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP3 Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/1.cellranger\_mkfastq\_nextseq.sh
RUN\_NUMBER

for example for run 103
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/1.cellranger\_mkfastq\_nextseq.sh
103

Once the demux is done the fastqs will be generated in the following
folder /ccbbdmxed/ca\_ns/lanecomment/OUTS/outs/fastq\_path/A*/*/\*gz

43

NextSeq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP4
Assemble the fastqs in a folder /ccbbdmxed/ca\_ns/lanecomment/
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/2.results\_fastqs.sh

After the execution of the above script you should see the following
folder with the fastqs and the md5 file

/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs

STEP5 INTERNAL Move the fastqs folder to the ftp location for dispatch
cd /ccbbftped/PIlastnamelab/ftp/seqdata/ rsync -avhP
/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs .

make sure the permissions are set correctly. “others” should have read
and execute permission on the folder and read permissions on the files
If the permissions are not ok use the following to set it

chmod o+rx lanecomment.tenxfastqs

cd lanecomment.tenxfastqs

chmod o+r \*

Sets the read and execute permissions for “others” for the 10X seqdata
folder for this dispatch. Sets the read permissions for “others” for the
all the files in the 10X seqdata folder for this dispatch. 44

NextSeq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP5

INTERNAL Move the fastqs folder to the ftp location for dispatch cd
/ccbbftped/PIlastnamelab/ftp/seqdata/ rsync -avhP
/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs .

make sure the permissions are set correctly. “others” should have read
and execute permission on the folder and read permissions on the files
If the permissions are not ok use the following to set it

chmod o+rx lanecomment.tenxfastqs

cd lanecomment.tenxfastqs

chmod o+r \*

Sets the read and execute permissions for “others” for the 10X seqdata
folder for this dispatch. Sets the read permissions for “others” for the
all the files in the 10X seqdata folder for this dispatch. 45

INTERNAL PROCESSED We usually put a processed folder(even if the lab did
not requests analysis).

cd /ccbbftped/PIlastnamelab/ftp/processed/ mkdir lanecomment chmod o+rx
lanecomment

cd lanecomment cp ../<contact_ccbb@scripps.edu>\_for\_analysis . chmod
o+r \*

REFER TO THE TEMPLATE EMAIL ON SLIDE 35 FOR INTERNAL 10X DATA DISPATCH

NextSeq 10X 5PR, 3PR, CMO

Sets the read and execute permissions for “others” for the processed
folder for this dispatch. 46

NextSeq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP5

EXTERNAL Move the fastqs folder to the ftp location for dispatch cd
/ccbbftped/PIlastnamelab/arrived/seqdata/ rsync -avhP
/ccbbdmxed/ca\_ns/lanecomment/lanecomment.tenxfastqs .

Create the tar for the 10X fastqs run folder tar -zcvf
lanecomment.tenxfastqs.tar lanecomment.tenxfastqs

Generate the MD5 for the tarred 10X fastqs folder md5sum
lanecomment.tenxfastqs.tar &gt; lanecomment.tenxfastqs.tar.md5

47

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP1
Assemble the BCLS in dispatch folder cd /ccbbftped/\*lab/arrived/bcls/

Copy the appropriate BCL run folder rsync -avhP
/ccbbbcled/nextseq2000/2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\* .

Rename the BCL run folder mv
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls

Create the tar for the BCL run folder tar -zcvf
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls

Generate the MD5 for the tarred BCL run folder md5sum
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar &gt;
2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar.md5

NextSeq 10X , Non 10X BCL DATA DISPATCH - External

48

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

cd to “transit place” where we rsync tar files from Step1 above:

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

rsync data for dispatch here md5 should be here –&gt;
/mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ tars should be here
–&gt; /mnt/oio/dnaarray/dispatch/disex/*lab/remote/

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/ rsync -avhP
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/bcls/2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar
.

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ rsync -avhP
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/bcls/2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar.md5
.

<https://www.computerhope.com/unix/rsync.htm>

NextSeq 10X , Non 10X BCL DATA DISPATCH - AWS 49

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE SCREEN SESSION)

STEP3 module load dis

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/

disexlist → This command lists the tar and md5 available in the external
customers AWS

disexcopy → This command copies the tar files using config file
remote.conf to the remote location
remote:scrippsresearchngscore-${company}

disexlist | grep “2\*\*\*\*\**VH00464*\*\*\*\_\*\*\*\*\*\*\*\*.bcls.tar”
→ check if the current dispatch files are copied

<https://rclone.org/>

Data Distribution - External BCL DATA DISPATCH - AWS 50

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP1
Assemble the BCLS in dispatch folder cd /ccbbftped/\*lab/arrived/bcls/

Copy the appropriate BCL run folder rsync -avhP
/ccbbbcled/novaseq6000/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*
.

Rename the BCL run folder mv
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls

Create the tar for the BCL run folder tar -zcvf
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls

Generate the MD5 for the tarred BCL run folder md5sum
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar &gt;
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5

Novaseq BCL DATA DISPATCH - External

51

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

cd to “transit place” where we rsync tar files from Step1 above:

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

rsync data for dispatch here md5 should be here –&gt;
/mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ tars should be here
–&gt; /mnt/oio/dnaarray/dispatch/disex/*lab/remote/

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/ rsync -avhP
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/bcls/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar
.

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ rsync -avhP
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/bcls/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5
.

<https://www.computerhope.com/unix/rsync.htm>

Novaseq BCL DATA DISPATCH - External 52

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE SCREEN SESSION)

STEP3 module load dis

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/

disexlist → This command lists the tar and md5 available in the external
customers AWS

disexcopy → This command copies the tar files using config file
remote.conf to the remote location
remote:scrippsresearchngscore-${company}

disexlist | grep
“2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar” → check if
the current dispatch files are copied

<https://rclone.org/>

Novaseq BCL DATA DISPATCH - External 53

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP1
Assemble the BCLS in dispatch folder cd /ccbbftped/\*lab/ftp/bcldata

Copy the appropriate BCL run folder rsync -avhP
/ccbbbcled/novaseq6000/2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*
.

Rename the BCL run folder mv
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls

Create the tar for the BCL run folder tar -zcvf
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls

Generate the MD5 for the tarred BCL run folder md5sum
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar &gt;
2\*\*\*\*\**A01255*\*\*\*\**\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5

Novaseq BCL DATA DISPATCH - Internal

54

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /gpfs/group/andersen/raw\_data

rsync data for dispatch here cd /gpfs/group/andersen/raw\_data rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/2*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar
.

cd /gpfs/group/andersen/raw\_data rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/2*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar.md5
.

Change the permissions of the copied files. chmod 777
2\*\*\*\*\**A01255*\*\*\*\*\_\*\*\*\*\*\*\*\*\*\*.bcls.tar\*

<https://www.computerhope.com/unix/rsync.htm>

Novaseq BCL DATA DISPATCH - Internal The following applies only to
andersenlab Novaseq runs 55

Novaseq 10X 5PR , 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP1 Create the directory for demux cd /ccbbdmxed/ca\_no mkdir
lanecomment for example : mkdir
ca\_no\_0244\_0?*0000\_0000\_lipton\_01*??-???-01-???

Change the permissions of the folder chmod 774 lanecomment cd
lanecomment

STEP2 create/ copy the samplesheet to the demux directory cd lanecomment

Use the WinSCP or Filezilla to move the samplesheet to the WS. The
samplesheet must be named csv.csv Just to be sure, we will change the
windows format text file to an unix format text file,
/home/ccbbguest/dos2unix csv.csv

Change the permissions of the samplesheet chmod 774 csv.csv

56

Novaseq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION)

STEP3 Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/Novaseq/1.mkfastq\_novaseq.sh
RUN\_NUMBER

for example for run 244
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/Novaseq/1.mkfastq\_novaseq.sh
244

Once the demux is done the fastqs will be generated in the following
folder /ccbbdmxed/ca\_no/lanecomment/OUTS/outs/fastq\_path/A*/*/\*gz

57

Novaseq 10X 5PR, 3PR, CMO

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP4
Assemble the fastqs in a folder /ccbbdmxed/ca\_no/lanecomment/
/ccbbdmxed/processed/benchmarking/scripts/10X\_mkfastq\_scripts/cellranger\_scripts/Novaseq/2.results\_fastqs.sh

After the execution of the above script you should see the following
folder with the fastqs and the md5 file

/ccbbdmxed/ca\_no/lanecomment/lanecomment.tenxfastqs

STEP5 Move the fastqs folder to the ftp location for dispatch (INTERNAL)
cd /ccbbftped/PIlastnamelab/ftp/seqdata/ rsync -avhP
/ccbbdmxed/ca\_no/lanecomment/lanecomment.tenxfastqs .

make sure the permissions are set correctly. “others” should have read
and execute permission on the folder and read permissions on the files
If the permissions are not ok use the following to set it

chmod o+rx lanecomment.tenxfastqs

cd lanecomment.tenxfastqs

chmod o+r \*

Sets the read and execute permissions for “others” for the 10X seqdata
folder for this dispatch. Sets the read permissions for “others” for the
all the files in the 10X seqdata folder for this dispatch. 58

INTERNAL PROCESSED We usually put a processed folder(even if the lab did
not requests analysis).

cd /ccbbftped/PIlastnamelab/ftp/processed/ mkdir lanecomment chmod o+rx
lanecomment

cd lanecomment cp ../<contact_ccbb@scripps.edu>\_for\_analysis . chmod
o+r \*

REFER TO THE TEMPLATE EMAIL ON SLIDE 35 FOR INTERNAL 10X DATA DISPATCH

Novaseq 10X 5PR, 3PR, CMO

Sets the read and execute permissions for “others” for the processed
folder for this dispatch. 59

BCL Data Backup Setup automatic login to Garibaldi

PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION You should be
able to login to Garibaldi using the following command WITHOUT using
your password:

The following steps are done only once for ccbbguest account on WS. STEP
1 ssh-keygen → Generate the authorized passkey for automatic login

The following steps are done only once per user. STEP 2 ssh-copy-id
<emailid@login00.scripps.edu> → Installs the SSH key from above on the
server.

ssh-copy-id <emailid@login02.scripps.edu>

ssh-copy-id <emailid@login03.scripps.edu>

STEP 3 Login to login00, login02 and login03 to check if you can login
without password.

<https://man.openbsd.org/ssh-keygen.1>
<https://www.ssh.com/academy/ssh/copy-id>

60

BCL Data Backup NextSeq 2000

STEP1 Before running the script,check to see enough space is available
for making tar files cd /ccbbbcled/nextseq2000

du -sh YYMM\* → To check the space taken by the run folders for Year and
Month du -sh 2309\* → To check the space taken by the run folders for
September 2023 df -h /ccbbbcled → To check how much space is available
in the ccbbbcled location.Check you have enough space before creating
the tar files.

STEP2 Prepare the BCL TARS for backup.

cd /ccbbbcled/nextseq2000 The arguments to the script is YEAR and MONTH.
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NextSeq/1.backup\_nextseq\_bcls\_step1\_prepare\_tars.sh
YY MM

For example for month of september for the year 2023, use the following
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NextSeq/1.backup\_bcls\_step1\_prepare\_tars.sh
23 09

Depending on the number of runs, size of the runs the above script
should take a while to complete. After the completion of the script, you
should see the *.tar and *.tar.md5 for the all the runs in the specified
month and year.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023. 61

BCL Data Backup NextSeq 2000

We will copy the BCL TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

STEP3 Copy the BCL TARS to OIO AND TAPE cd
/ccbbbcled/nextseq2000/dnaarray-bcled-nex2k-0vh00464/

/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NextSeq/2.backup\_nextseq\_bcls\_step2\_copy\_tars\_to\_OIO.sh

Depending on the number of runs, size of the runs the above script
should take a while to complete.

STEP4 After the copy is done , verify that the bcls are present in the
OIO location. module load rclone disoslist | grep “YYMM” → check if the
current dispatch files are copied to the OIO

For example for the September , 2023 data use the following disoslist |
grep “2309”

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) 62

BCL Data Backup NextSeq 2000

STEP5 After successful copy of BCL data to OIO, Update the BCL backup
excel with the relevant details. Please share the excel sheet with CCBB.

Example sheet here :
<https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0>

STEP6 Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list
of runs that were backed up. After this , the backed up runs will be
deleted from FreeNAS by JC. (PLEASE DO ALL THE FOLLOWING STEPS INSIDE
THE BYOBU SESSION) 63

BCL Data Backup NovaSeq 6000

STEP1 Before running the script,check to see enough space is available
for making tar files cd /ccbbbcled/novaseq6000

du -sh YYMM\* → To check the space taken by the run folders for Year and
Month du -sh 2310\* → To check the space taken by the run folders for
October 2023 df -h /ccbbbcled → To check how much space is available in
the ccbbbcled location.Check you have enough space before creating the
tar files.

STEP2 Prepare the BCL TARS for backup.

cd /ccbbbcled/novaseq6000 The arguments to the script is YEAR and MONTH.
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NovaSeq/1.backup\_novaseq\_bcls\_step1\_prepare\_tars.sh
YY MM

For example for month of september for the year 2023, use the following
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NovaSeq/1.backup\_novaseq\_bcls\_step1\_prepare\_tars.sh
23 10

Depending on the number of runs, size of the runs the above script
should take a while to complete. After the completion of the script, you
should see the *.tar and *.tar.md5 for the all the runs in the specified
month and year.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP as soon as the demux is done or in case of BCL
dispatch as soon as it is dispatched. 64

BCL Data Backup NovaSeq 6000

We will copy the BCL TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

STEP3 Copy the BCL TARS to OIO AND TAPE cd
/ccbbbcled/novaseq6000/dnaarray-bcled-nov6k-00a01255

/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/NovaSeq/2.backup\_novaseq\_bcls\_step2\_copy\_tars\_to\_OIO.sh

Depending on the number of runs, size of the runs the above script
should take a while to complete.

STEP4 After the copy is done , verify that the bcls are present in the
OIO location. module load rclone disoslist | grep “YYMM” → check if the
current dispatch files are copied to the OIO

For example for the October , 2023 data use the following disoslist |
grep “2310”

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) 65

BCL Data Backup NovaSeq 6000

STEP5 After successful copy of BCL data to OIO, Update the BCL backup
excel with the relevant details. Please share the excel sheet with CCBB.

Example sheet here :
<https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0>

STEP6 Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list
of runs that were backed up. After this , the backed up runs will be
deleted from FreeNAS by JC. (PLEASE DO ALL THE FOLLOWING STEPS INSIDE
THE BYOBU SESSION) 66

DEMUXED Data Backup NextSeq 2000

STEP1 Before running the script,check to see enough space is available
for making tar files cd /ccbbdmxed/ca\_ns/dispatch

du -sh YYYYMM\* → To check the space taken by the run folders for Year
and Month du -sh 202309\* → To check the space taken by the run folders
for September 2023 df -h /ccbbdmxed/ → To check how much space is
available in the ccbbdmxed location.Check you have enough space before
creating the tar files.

STEP2 Prepare the DEMUX TARS for backup.

cd /ccbbdmxed/ca\_ns/dispatch The arguments to the script is YEAR and
MONTH.
/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/NextSeq/1.backup\_nextseq\_dmxed\_step1\_prepare\_tars.sh
YYYY MM

For example for month of september for the year 2023, use the following
/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/NextSeq/1.backup\_nextseq\_dmxed\_step1\_prepare\_tars.sh
2023 09

Depending on the number of runs, size of the runs the above script
should take a while to complete. After the completion of the script, you
should see the *.tar and *.tar.md5 for the all the runs in the specified
month and year.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023. 67

DEMUXED Data Backup NextSeq 2000

We will copy the DEMUX TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

STEP3 Copy the DEMUXED TARS to OIO AND TAPE cd
/ccbbdmxed/ca\_ns/dispatch/dnaarray-dmxed-ns–0000to0099

/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/NextSeq/2.backup\_nextseq\_dmxed\_step2\_copy\_tars\_to\_OIO.sh

Depending on the number of runs, size of the runs the above script
should take a while to complete.

STEP4 After the copy is done , verify that the DEMUXED TARS are present
in the OIO location. module load rclone disoslist | grep “YYYYMM” →
check if the current dispatch files are copied to the OIO

For example for the September , 2023 data use the following disoslist |
grep “202309”

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) 68

DEMUXED Data Backup NextSeq 2000

STEP5 After successful copy of DEMUX data to OIO, Update the excel with
the relevant details. Please share the excel sheet with CCBB.

Example sheet here :
<https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0>

STEP6 Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list
of DEMUXED RUNS that were backed up. After this , the backed up runs
will be deleted from FreeNAS by JC. (PLEASE DO ALL THE FOLLOWING STEPS
INSIDE THE BYOBU SESSION) 69

Sample sheet

Example samplesheet (aviti) available at

TEMPLATE AVITI SAMPLESHEEET

STEP1 Use the WinSCP or Filezilla to move the samplesheet to the WS in
the directory /ccbbdmxed/ca\_av/fromlims

cd /ccbbdmxed/ca\_av/fromlims (change directory)

mv samplesheet.csv ca\_av\_0???.samplesheet.csv (make sure to name the
file with the appropriate run number) For example for run ca\_av\_0003
mv samplesheet.csv ca\_av\_0003.samplesheet.csv

Change the permissions of the samplesheet chmod 775
ca\_av\_0???.samplesheet.csv

Just to be sure, we will change the windows format text file to an unix
format text file, /home/ccbbguest/dos2unix ca\_av\_0003.samplesheet.csv

AVITI Last Updated : November 07, 2023 70

AVITI STEP2 The sequencing data for AVITI is mapped to the workstations
in the following location /ccbbbcled/aviti/AV233601

The data should be mapped to this location instead /ccbbbcled/aviti/

So copy the run data to the desired location. Always copy the run data
“NOT ENDING IN PRIME” cd /ccbbbcled/aviti/ rsync -avhP
/ccbbbcled/aviti/AV233601/20\*\*\*\*\*\**AV233601\_ca\_av\_0\*\*\*\**\*\*\*\*\*\*\*\**\*\*\*\**\*\*\*\*
.

for example for run ca\_av\_0003 cd /ccbbbcled/aviti/ rsync -avhP
/ccbbbcled/aviti/AV233601/20231103\_AV233601\_ca\_av\_0003\_20231103\_10X\_high
.

Check if the folder is copied. ls
/ccbbbcled/aviti/20\*\*\*\*\*\**AV233601\_ca\_av\_0\*\*\*\**\*\*\*\*\*\*\*\**\*\*\*\**\*\*\*\*

Once the rync is rename the folder. The current run folder for aviti
contains non standard naming conventions. cd /ccbbbcled/aviti/ mv
20\*\*\*\*\*\**AV233601\_ca\_av\_0\*\*\*\**\*\*\*\*\*\*\*\**\*\*\*\**\*\*\*\*
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*

for example for run ca\_av\_0012 mv
20231212\_AV233601\_ca\_av\_0012\_20231212\_mendoza\_AM\_high
20231212\_AV233601\_ca\_av\_0012

Remove the BCL folder ONLY from the following directory after dispatch
/ccbbbcled/aviti/ Last Updated : December 13, 2023 71

AVITI

STEP3

cd /ccbbdmxed/ca\_av

Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/1.ccbbdemux\_aviti.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/1.ccbbdemux\_aviti.sh
ca\_av\_0003

Last Updated : November 07, 2023 Dual Index Samples 72

AVITI

STEP3

cd /ccbbdmxed/ca\_av

Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/1a.ccbbdemux\_aviti\_single\_index.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/1a.ccbbdemux\_aviti\_single\_index.sh
ca\_av\_0003

Last Updated : December 06, 2023 Single Index Samples 73

AVITI

cd /ccbbdmxed/ca\_av

Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/2.ccbbdemux\_aviti\_qc\_only.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/2.ccbbdemux\_aviti\_qc\_only.sh
ca\_av\_0003

Last Updated : January 03, 2024 Dual Index Samples - QC ONLY Enable
QC-only mode, which generates a representative view of run metrics on
one tile and no FASTQ files. 74

AVITI

cd /ccbbdmxed/ca\_av

Run the demux script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/2a.ccbbdemux\_aviti\_single\_index\_qc\_only.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/2a.ccbbdemux\_aviti\_single\_index\_qc\_only.sh
ca\_av\_0003

Last Updated : January 03, 2024 Single Index Samples- QC ONLY Enable
QC-only mode, which generates a representative view of run metrics on
one tile and no FASTQ files.

75

AVITI INTERNAL DISPATCH

Dual Index Samples

STEP4 Copy the fastqs to FTP for dispatch and generate email for
dispatch

cd /ccbbdmxed/ca\_av

Run the following script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/3.ccbbdemux\_aviti\_results\_to\_ftp.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/3.ccbbdemux\_aviti\_results\_to\_ftp.sh
ca\_av\_0003

After the successful running of this script the seqdata and QC will be
copied to the /ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment and
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment\_IndexAssignment.csv
respectively.

The processed data folder will be created in the
/ccbbftped/PIlastnamelab/ftp/processed/lanecomment location.

The dispatch emails will also be generated with the ftp links. Last
Updated : January 22, 2024 76

AVITI INTERNAL DISPATCH

Single Index Samples

STEP4 Copy the fastqs to FTP for dispatch and generate email for
dispatch

cd /ccbbdmxed/ca\_av

Run the following script giving it the run number as parameter
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/3a.ccbbdemux\_aviti\_single\_index\_results\_to\_ftp.sh
ca\_av\_RUN\_NUMBER

for example for run ca\_av\_0003
/ccbbdmxed/processed/benchmarking/scripts/AVITI\_demux\_scripts/3a.ccbbdemux\_aviti\_single\_index\_results\_to\_ftp.sh
ca\_av\_0003

After the successful running of this script the seqdata and QC will be
copied to the /ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment and
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment\_IndexAssignment.csv
respectively.

The processed data folder will be created in the
/ccbbftped/PIlastnamelab/ftp/processed/lanecomment location.

The dispatch emails will also be generated with the ftp links. Last
Updated : January 22, 2024 77

After the demux is done , the seqdata, QC gets copied to the ftp server
for dispatch.

The seqdata goes to the following location
/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment

The QC data goes to the following location
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment\_IndexAssignment.csv

Once the data is verified - QC is ok ( either passed/missed) , no
barcode clashes etc) The data needs to be moved to the ftp location for
dispatch

SEQDATA cd /ccbbftped/PIlastnamelab/ftp/seqdata/ mv
/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment . make sure the
permissions are set correctly. “others” should have read and execute
permission on the folder and read permissions on the files If the
permissions are not ok use the following to set it

chmod o+rx lanecomment

cd lanecomment

chmod o+r \* Data Distribution - Internal

Sets the read and execute permissions for “others” for the seqdata
folder for this dispatch. Sets the read permissions for “others” for the
all the files in the seqdata folder for this dispatch. Last Updated :
January 22, 2024 78

QC

cd /ccbbftped/PIlastnamelab/ftp/qc/ mv
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment\_IndexAssignment.csv .
make sure the permissions are set correctly. “others” should have read
permissions on the QC file If the permissions are not ok use the
following to set it

chmod o+r lanecomment\_IndexAssignment.csv

PROCESSED We usually put a processed folder(even if the lab did not
requests analysis).

The processed folder is created by the script in the following location.
/ccbbftped/PIlastnamelab/ftp/processed/lanecomment

STEP5 Dispatch the data Use the email template and dispatch the data.
Edit links as needed. Make sure the ftp hyperlinks are functional.

STEP6 Remove the BCL folder ONLY from the following directory after
dispatch /ccbbbcled/aviti/

Data Distribution - Internal

Last Updated : January 22, 2024 79

We will dispatch the BCL only if the flowcell/run is not shared with any
other lab/company  
If the run is shared with multiple labs we need permission from all the
PI’s in the run to share the BCL data.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) STEP1
Assemble the BCLS in dispatch folder cd /ccbbftped/\*lab/ftp/bcldata

Copy the appropriate BCL run folder rsync -avhP
/ccbbbcled/aviti/20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\* .

Rename the BCL run folder mv 20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls

Create the tar for the BCL run folder tar -zcvf
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls

Generate the MD5 for the tarred BCL run folder md5sum
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar &gt;
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar.md5

AVITI BCL DATA DISPATCH - Internal

Last Updated : December 18, 2023 80

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /gpfs/group/andersen/raw\_data

rsync data for dispatch here cd /gpfs/group/andersen/raw\_data rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/20*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar
.

cd /gpfs/group/andersen/raw\_data rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/ftp/bcldata/20*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar.md5
.

Change the permissions of the copied files. chmod 777
20\*\*\*\*\*\*\_AV233601\_ca\_av\_0\*\*\*\*.bcls.tar\*

<https://www.computerhope.com/unix/rsync.htm>

AVITI BCL DATA DISPATCH - Internal The following applies only to
andersenlab runs Last Updated : December 18, 2023 81

AVITI Data Distribution - External AWS After the demux is done , the
seqdata, QC gets copied to the ftp server for dispatch.

The seqdata and QC goes to the following location
/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment

Once the data is verified - QC is ok The data needs to be moved to the
garibaldi location for dispatch (PLEASE DO ALL THE FOLLOWING STEPS
INSIDE THE BYOBU SESSION)

Prepare the seqdata folder before transferring to garibaldi cd
/ccbbftped/PIlastnamelab/arrived/seqdata/ mv lanecomment
lanecomment.fastqs

tar -zcvf lanecomment.fastqs.tar lanecomment.fastqs

md5sum lanecomment.fastqs.tar &gt; lanecomment.fastqs.tar.md5

82

STEP2 Gather data at the external dispatch location on Garibaldi login
to login03.scripps.edu ssh <scrippsid@login03.scripps.edu>

cd to “transit place” where we rsync tar files from Step1 above:

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

screen → To open a session (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
SCREEN SESSION) control+A+D → To detach a session screen -r → To resume
a session

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/remote

rsync data for dispatch here md5 should be here –&gt;
/mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ tars should be here
–&gt; /mnt/oio/dnaarray/dispatch/disex/*lab/remote/

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar
.

cd /mnt/oio/dnaarray/dispatch/disex/*lab/remote/md5/ rsync -av
<ccbbguest@ccbbstation04.scripps.edu>:/ccbbftped/*lab/arrived/seqdata/lanecomment.fastqs.tar.md5
.

<https://www.computerhope.com/unix/rsync.htm>

AVITI Data Distribution - External AWS 83

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE SCREEN SESSION)

STEP3 module load dis

cd /mnt/oio/dnaarray/dispatch/disex/\*lab/

disexlist → This command lists the tar and md5 available in the external
customers AWS

disexcopy → This command copies the tar files using config file
remote.conf to the remote location
remote:scrippsresearchngscore-${company}

disexlist | grep ‘lanecomment’ → check if the current dispatch files are
copied

<https://rclone.org/>

AVITI Data Distribution - External AWS 84

BCL Data Backup AVITI

STEP1 Before running the script,check to see enough space is available
for making tar files cd /ccbbbcled/aviti

du -sh YYMM\* → To check the space taken by the run folders for Year and
Month du -sh 2309\* → To check the space taken by the run folders for
September 2023 df -h /ccbbbcled → To check how much space is available
in the ccbbbcled location.Check you have enough space before creating
the tar files.

STEP2 Prepare the BCL TARS for backup.

cd /ccbbbcled/aviti/AV233601 The arguments to the script is YEAR and
MONTH.
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/AVITI/1.backup\_aviti\_bcls\_step1\_prepare\_tars.sh
YYYY MM

For example for month of October for the year 2023, use the following
/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/AVITI/1.backup\_aviti\_bcls\_step1\_prepare\_tars.sh
2023 10

Depending on the number of runs, size of the runs the above script
should take a while to complete. After the completion of the script, you
should see the *.tar and *.tar.md5 for the all the runs in the specified
month and year in this location
/ccbbbcled/aviti/dnaarray-bcled-aviti-av233601

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023. 85

BCL Data Backup AVITI

We will copy the BCL TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

STEP3 Copy the BCL TARS to OIO AND TAPE cd
/ccbbbcled/aviti/dnaarray-bcled-aviti-av233601

/ccbbdmxed/processed/benchmarking/scripts/BCL\_backup\_scripts/AVITI/2.backup\_aviti\_bcls\_step2\_copy\_tars\_to\_OIO.sh

Depending on the number of runs, size of the runs the above script
should take a while to complete.

STEP4 After the copy is done , verify that the bcls are present in the
OIO location. module load rclone disoslist | grep “YYYYMM” → check if
the current dispatch files are copied to the OIO

For example for the October , 2023 data use the following disoslist |
grep “202310”

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) 86

BCL Data Backup AVITI

STEP5 After successful copy of BCL data to OIO, Update the BCL backup
excel with the relevant details. Please share the excel sheet with CCBB.

Example sheet here :
<https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0>

STEP6 Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list
of runs that were backed up. After this , the backed up runs will be
deleted from FreeNAS by JC. (PLEASE DO ALL THE FOLLOWING STEPS INSIDE
THE BYOBU SESSION) 87

DEMUXED Data Backup AVITI

STEP1 Before running the script,check to see enough space is available
for making tar files cd /ccbbdmxed/ca\_av/dispatch

du -sh YYYYMM\* → To check the space taken by the run folders for Year
and Month du -sh 202310\* → To check the space taken by the run folders
for October 2023 df -h /ccbbdmxed/ → To check how much space is
available in the ccbbdmxed location.Check you have enough space before
creating the tar files.

STEP2 Prepare the DEMUX TARS for backup.

cd /ccbbdmxed/ca\_av/dispatch The arguments to the script is YEAR and
MONTH.
/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/AVITI/1.backup\_AVITI\_dmxed\_step1\_prepare\_tars.sh
YYYY MM

For example for month of september for the year 2023, use the following
/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/AVITI/1.backup\_AVITI\_dmxed\_step1\_prepare\_tars.sh
2023 09

Depending on the number of runs, size of the runs the above script
should take a while to complete. After the completion of the script, you
should see the *.tar and *.tar.md5 for the all the runs in the specified
month and year.

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) START THE
PROCESS OF BACKUP for the previous month by 10th of the following month,
For example start the backup of BCL process of all September 2023 runs
by 10th of October 2023. 88

DEMUXED Data Backup AVITI

We will copy the DEMUX TARS to two locations as a part of the backup
process. OIO - object storage TAPE - physical tapes - CCBB will take
care of tape backup for now.

STEP3 Copy the DEMUXED TARS to OIO AND TAPE cd
/ccbbdmxed/ca\_av/dnaarray-dmxed-av–0000to0099

/ccbbdmxed/processed/benchmarking/scripts/DEMUX\_backup\_scripts/AVITI/2.backup\_aviti\_dmxed\_step2\_copy\_tars\_to\_OIO.sh

Depending on the number of runs, size of the runs the above script
should take a while to complete.

STEP4 After the copy is done , verify that the DEMUXED TARS are present
in the OIO location. module load rclone disoslist | grep “YYYYMM” →
check if the current dispatch files are copied to the OIO

For example for the October , 2023 data use the following disoslist |
grep “202310”

(PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) 89

DEMUXED Data Backup AVITI

STEP5 After successful copy of DEMUX data to OIO, Update the excel with
the relevant details. Please share the excel sheet with CCBB.

Example sheet here :
<https://docs.google.com/spreadsheets/d/1zdbYyDZKTaKKJNoxiTiLe1gf7A_2UUL8RY20HmIocXc/edit#gid=0>

STEP6 Email <ccbb@scripps.edu> and <jcducom@scripps.edu> with the list
of DEMUXED RUNS that were backed up. After this , the backed up runs
will be deleted from FreeNAS by JC. (PLEASE DO ALL THE FOLLOWING STEPS
INSIDE THE BYOBU SESSION) 90

NovaSeq - Demux

Read lengths sequenced should be EXACT as needed by the project.

91

Run Type Comments NextSeq (general projects) Training completed NextSeq
(10x projects) Training completed for both 10X Multiome and 10X Non
Multiome (5PR, 3PR, CMO) NovaSeq (10x projects) Training completed for
10X Non Multiome (5PR, 3PR, CMO) Demux Data Dispatch Training completed
for both Internal and External BCL Data Dispatch Training completed for
both Internal and External NextSeq and NovaSeq BCL Backup Process
Training completed NextSeq and NovaSeq Demux data Backup Process
Training completed AVITI (general projects 10X and Non 10X) Training
completed. Single and Dual index demux Single and Dual index QC only
Demux Demux data copy to ftp and template email generation NovaSeq (Non
10x projects) NextSeq (GeoMX projects) to be discussed AVITI (general
projects) to be discussed
<https://docs.google.com/spreadsheets/d/1HQuYMpRm16iSapAydSDJXnwe1Hzay1-noGtUw3AY-K0/edit#gid=0>
92

Data Distribution - External ONEDRIVE After the demux is done , the
seqdata, QC gets copied to the ftp server for dispatch.

The seqdata goes to the following location
/ccbbftped/PIlastnamelab/arrived/seqdata/lanecomment

The QC data goes to the following location
/ccbbftped/PIlastnamelab/arrived/qc/lanecomment

Once the data is verified - QC is ok ( either passed/missed) , no
barcode clashes etc) The data needs to be moved to the garibaldi
location for dispatch (PLEASE DO ALL THE FOLLOWING STEPS INSIDE THE
BYOBU SESSION)

STEP1 Prepare the seqdata folder before transferring to garibaldi cd
/ccbbftped/PIlastnamelab/arrived/seqdata/

mv lanecomment lanecomment.fastqs

tar -zcvf lanecomment.fastqs.tar lanecomment.fastqs

md5sum lanecomment.fastqs.tar &gt; lanecomment.fastqs.tar.md5

93

STEP2

SET UP RCLONE FOR ONEDRIVE
<https://docs.google.com/document/d/1iiHQNafugXtln1wwPVJGUduQc51ZRFG7lPZMLXw68r4/edit>
<https://rclone.org/onedrive/>

cd to “transit place” where we rsync tar files from Step1 above: (PLEASE
DO ALL THE FOLLOWING STEPS INSIDE THE BYOBU SESSION) cd
/ccbbftped/PIlastnamelab/arrived/seqdata/

module load rclone unset RCLONE\_CONFIG rclone listremotes

Below output are specific to me (Aishwarya): List directories in top
level of your OneDrive: rclone lsd AS\_onedrive: List all the files in
your OneDrive: rclone ls AS\_onedrive:

rclone mkdir AS\_onedrive:PIlastnamelab rclone copy –progress
lanecomment.fastqs.tar AS\_onedrive:PIlastnamelab

rclone copy –progress lanecomment.fastqs.tar.md5
AS\_onedrive:PIlastnamelab

Data Distribution - External ONEDRIVE 94

AVITI INTERNAL DISPATCH STEP4 Copy the fastqs to FTP for dispatch
SEQDATA cd /ccbbftped/PIlastnamelab/ftp/seqdata/ mkdir Project ie ,
mkdir
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials
for example for run ca\_av\_0014 , mkdir
ca\_av\_0014\_nemazee\_20231205\_0\_10X5prime\_mouse\_MO chmod o+rx
Project ie , chmod o+rx
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials
cd
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials

Copy the FASTQS from the DEMUXXED LOCATION rsync -avhP
/ccbbdmxed/ca\_av/20??????\_AV233601\_ca\_av\_00??/ccbbdemux/Samples/ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials/*/*.gz
.

check if the fastqs are copied , ls \*.gz

Generate the MD5SUM for the fastqs md5sum \*.gz &gt;
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials.md5sum

make sure the permissions are set correctly. “others” should have read
permissions on the all files If the permissions are not ok use the
following to set it

chmod o+r \*

Last Updated : December 19, 2023 95

AVITI INTERNAL DISPATCH STEP4 QC cd /ccbbftped/PIlastnamelab/ftp/qc/
Copy the QC from the DEMUXXED LOCATION rsync -avhP
/ccbbdmxed/ca\_av/20??????\_AV233601\_ca\_av\_00??/ccbbdemux/Samples/ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials/\*IndexAssignment.csv
. make sure the permissions are set correctly. “others” should have read
permissions on the QC file If the permissions are not ok use the
following to set it

chmod o+r
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials\_IndexAssignment.csv

PROCESSED We usually put a processed folder(even if the lab did not
requests analysis).

cd /ccbbftped/PIlastnamelab/ftp/processed/ mkdir Project ie , mkdir
ca\_av\_00??\_PIlastname\_YYYYMMDD\_0\_exptType\_species\_contactFirstLastInitials

for example for run ca\_av\_0014 , mkdir
ca\_av\_0014\_nemazee\_20231205\_0\_10X5prime\_mouse\_MO

chmod o+rx lanecomment

cd lanecomment cp ../<contact_ccbb@scripps.edu>\_for\_analysis . chmod
o+r \*

Last Updated : December 19, 2023 Sets the read and execute permissions
for “others” for the processed folder for this dispatch. 96

=============================================

This is related to your sequencing project, project name- run-

Internal Data Dispatch:

Instructions to access the data dispatched:
<https://github.com/ScrippsCCBB/CCBBwebsite/blob/main/FileZilla_Instructions_CCBB.pdf>

Please download your processed data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/processed/ca_av_000?_PIlastname_YYYYMMDD_0_exptType_species_contactFirstLastInitials/>

Please download your qc data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/qc/>

Please download your sequencing data from the following link:
<ftp://PIlastnamelab:PIlastnamelab@shulik.scripps.edu/seqdata/ca_av_000?_PIlastname_YYYYMMDD_0_exptType_species_contactFirstLastInitials/>

AVITI INTERNAL DISPATCH STEP5 Dispatch the data This is a template. Edit
the PI lastname , run name etc in the links before dispatch. Use the
following email template 97
