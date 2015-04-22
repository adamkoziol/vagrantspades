### olcbioinformatics/vagrantspades

Docker image for running the spades pipeline on data in a mounted volume, capable of being run on vagrant.

To obtain the image, either pull from the public repository:

# sudo docker pull olcbioinformatics/vagrantspades

or place the Dockerfile in a directory and build the image locally, in which case you first need the ubuntu:14.04 base image:
# sudo docker pull ubuntu:14.04

# sudo docker build -t olcbioinformatics/vagrantspades /path/to/Dockerfile/directory/
 
The container will require a mounted volume containing the data sets to be run.
This can have any name on the host machine, but within the container must be named
/mnt/zvolume1/WGS_Spades until further notice.

# mkdir /path/to/datavolume

You can then put data folders in this volume at your leisure, even while the
container is mounted. Each data folder inside the volume should contain fastq files
and the three files:
SampleSheet.csv
RunInfo.xml
GenerateFASTQRunStatistics.xml
See the spades pipeline README available at https://github.com/adamkoziol/SPAdesPipeline/blob/master/README.md
for details.

To create the container with the volume mounted, use:
# sudo docker run -it -v /path/to/datavolume:/mnt/zvolume1/WGS_Spades olcbioinformatics/vagrantspades

Which will put you in a bash shell within the container. To run a datafolder through the pipeline:
#> SPAdesPipeline.py -p /mnt/zvolume1/WGS_Spades/datafolder 

