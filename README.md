# Earth-523
This is a tutorial describing metagenomic basic analysis for MABR suspended vs biofilm samples.

General Help:
General metagenomic tutorial from a different university: https://github.com/LangilleLab/microbiome_helper/wiki/Metagenomics-Tutorial-(Humann2)

Flux tutorial: https://arc-ts.umich.edu/flux-user-guide/

WinSCP Help: https://documentation.its.umich.edu/node/349

Greg's lab's protocols" file:///C:/Users/bmwag/Downloads/Geomicro-Illumina-Reads-Processing-Pipeline%20(1).pdf

Etherpad from software carpentry: https://pad.carpentries.org/2019-03-04-umich-genomics

Microbiol 612 class github: https://github.com/alipirani88/Comparative_Genomics

NCyc nitrogen gene database: https://github.com/qichao1984/NCyc



To access Michigan flux account via Windows + Putty:
Open putty:
Under host name/IP address: type “flux-login.arc-ts.umich.edu”
Under connection – ssh – x11 in the left column: Enable x-11 forwarding
yes at putty security if it pops up

Once in putty: type uniquename (do not add @umich.edu)


To transfer data to flux account:

Use WinSCP
1. On WinSCP, set Hostname = flux-xfer.arc-ts.umich.edu and input flux username and password
2. On the right half of the window (future location of flux files), go to the file location selection near the top and go to the / <root> folder
3. On / <root>, go to scratch folder, then engin_flux folder, then your unique name  
4. Transfer files by dragging their icons from one side of the window to the other . You can copy files from your local computer to your AFS home directory and vice versa. Note this can take several hours (1.5 hours for 30gb).

Data:
Data received from a sequencer is in a map file.  Raw data is in fastq format within the map file.  Map or fastq files are gunzipped to save space


To begin with flux, you must add the geomicro repository (in order to use Greg's commands provided from his help document)
1. Point at the Geo modules: type "module use -a /dept/geology/geomicro/data9/flux/modulefiles"
2. Load the Geo modules: type "module load geomicro/omics"
3. Save this as a default module so it will be automatically loaded each time you login: type "module save"

To view the files that you added to flux scratch
1. type: "cd /scratch/engin_flux/brettwag" (cd = change directory (file))
    other helpful command type "pwd" to show the name of the present working directory (which file that you're in)
                          type "ls" to show what files are located in your pwd
                          
To submit a job to flux:
Use the following format to create a .pbs file which can be submitted as a job

#Header

#PBS -N "NAME INSERT HERE"
#PBS -A earth523w19_fluxm
#PBS -q fluxod
#PBS -l nodes=1:ppn=4,pmem=4GB,walltime=1:00:00,qos=flux
#PBS -M brettwag@umich.edu
#PBS -m abe
#PBS -j oe
#PBS -V

if [ "x${PBS_NODEFILE}" != "x" ] ; then
        cat $PBS_NODEFILE
fi

cd $PBS_O_WORKDIR
echo $PBS_O_WORKDIR

#Code goes here

bash fastqc.sh /scratch/micro612w19_fluxod/shared/data/day3_after_fastq/


Sequencing pipeline:
1. load the geomicro container by typing: "comics"
2. type "gunzip Biofilm1_94978_AGTCAA_S13_L002_R*" while in the folder where your data is located to remove the gunzip format from all the files within the folder (took around 15 min but can be less/more) (shown in photo 1)
3. rename the files to fwd.fastq and rev.fastq in order to use the Greg's guide by typing: "mv Biofilm1_94978_AGTCAA_S13_L002_R1_001.fastq fwd.fastq" where "mv [old file name] [new file name]" R1 = fwd R2 = rev






                       
    


