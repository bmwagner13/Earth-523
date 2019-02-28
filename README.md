# Earth-523
metagenomic basics + MABR suspended vs biofilm metagenomic analysis

General Help:
General tutorial from a different university: https://github.com/LangilleLab/microbiome_helper/wiki/Metagenomics-Tutorial-(Humann2)
Flux tutorial: https://arc-ts.umich.edu/flux-user-guide/
WinSCP Help: https://documentation.its.umich.edu/node/349

Data:
Data received from a sequencer is in a map file.  Raw data is in fastq format within the map file.  Map or fastq files are gunzipped to save space

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
4. Transfer files by dragging their icons from one side of the window to the other . You can copy files from your local computer to your AFS home directory and vice versa.  

