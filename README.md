![alt text](https://arimagenomics.com/wp-content/files/2021/08/Arima-Genomics-logo.png "Celebrating Science and Scientist")

# Docker and Singularity images of Juicer pipeline
To order Arima kits, please visit our website:
https://arimagenomics.com/

# Getting Started
We provide both Docker and Singularity container implementations of the Juicer pipeline for users to run Juicer out of the box.

# Install Docker or Singularity
## Docker
https://docs.docker.com/engine/install/
## Singularity
https://docs.sylabs.io/guides/3.0/user-guide/index.html

# Download links
## Docker
```
docker pull arimaxiang/arima_juicer:1.6
```

## Singularity
```
wget ftp://ftp-arimagenomics.sdsc.edu/pub/Juicer_pipeline_containers/juicer-1.6.sif
```

# Usage
## If you are using Docker
Please refer to our Docker page: https://hub.docker.com/r/arimaxiang/arima_juicer

## If you are using Singularity
```
# module load singularitypro (Make sure you have singularity tool in your environment. You may need to use a different command depending on your settings)
OUTPUT_DIR="your_output_directory_path"
mkdir $OUTPUT_DIR/fastq/
mv test_sample_R*.fastq.gz $OUTPUT_DIR/fastq/  # Put your raw FASTQ files in a subfolder named "fastq" under $OUTPUT_DIR
INPUT_reference="put_all_reference_and_accessory_files_here"
singularity exec -B $OUTPUT_DIR -B $INPUT_reference juicer-1.6.sif juicer.sh -d $OUTPUT_DIR -D /opt/ -p $INPUT_reference/hg38.chrom.sizes -y $INPUT_reference/hg38_GATC_GANTC.txt -z $INPUT_reference/hg38.fa -t 20 &> $OUTPUT_DIR"/juicer.log"
```

Detailed Juicer pipeline usage can be found at: https://github.com/aidenlab/juicer/wiki/Usage

# Current Version
The Docker and Singularity images were built based on Juicer v1.6 (https://github.com/aidenlab/juicer/releases/tag/1.6)

# Release Note
- This version fixed the long-standing issue of the original Docker image: https://github.com/theaidenlab/Juicer-Docker/issues/2
- Updated some tools and dependencies to the more stable and more recent versions.

# Acknowledgments
#### Authors of Juicer: https://github.com/aidenlab/juicer
- Neva C. Durand, Muhammad S. Shamim, Ido Machol, Suhas S. P. Rao, Miriam H. Huntley, Eric S. Lander, and Erez Lieberman Aiden. "Juicer provides a one-click system for analyzing loop-resolution Hi-C experiments." Cell Systems 3(1), 2016.


