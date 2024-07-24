## pipeline [structure](https://nf-co.re/docs/contributing/pipelines/pipeline_file_structure)

nf-core [install](https://nf-co.re/docs/nf-core-tools/installation)
```
pip install  --upgrade nf-core
```

template [pipeline](https://nf-co.re/docs/nf-core-tools/pipelines/create)
```
nf-core create
cd nf-core-quantifyprotein/
```

create [repo](https://github.com/animesh/nf-core-quantifyprotein)
```
git remote add origin https://github.com/animesh/nf-core-quantifyprotein.git
git checkout dev
git status
git push --all origin
#git push --set-upstream origin dev
```

nextflow [download](https://nextflow.io/example5.html)
```
curl -fsSL get.nextflow.io | bash
nextflow  -v
./nextflow self-update
nextflow  -v
```

docker [install](https://docs.docker.com/engine/install/ubuntu/)
```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker erd runc; do sudo apt-get remove $pkg; done
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
# Add the repository to Apt sources:
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.tps://download.docker.com/linux/ubuntu \
etc/os-release && echo "$VERSION_CODENAME") stable" |   sudo tee /etc/apt/sources.docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin compose-plugin
sudo docker run hello-world
```


[test](https://nf-co.re/docs/usage/introduction#how-to-run-a-pipeline)
```
 ./nextflow run hello
sudo ./nextflow run nf-core/rnaseq -profile test,docker --outdir test #-resume e.g., result1 file://wsl.localhost/Ubuntu/home/ash022/nf-core-quantifyprotein/test/fastqc/SAMPLE1_PE_1_fastqc.html
```

[DDA](https://github.com/animesh/scripts/blob/master/scratch.slurm)
```
wget "https://server-share.promec.sigma2.no/raw/HeLa.tar?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=4VFDSD3OB6SBSJAASVXZ%2F20240723%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240723T131419Z&X-Amz-Expires=604800&X-Amz-Security-Token=eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJhY2Nlc3NLZXkiOiI0VkZEU0QzT0I2U0JTSkFBU1ZYWiIsImV4cCI6MTcyMTc0Mzk1MywicGFyZW50IjoicHJvbWVjc2hhcmUifQ.DTcGnBLlkwHgdRlcGUIkDtOVCjf2Ke73MreQAj1ciO21IMVMM8Vq8zbYwYBgG8DBnES7hzMoSL5Vm6Mvpz8mHQ&X-Amz-SignedHeaders=host&versionId=null&X-Amz-Signature=5abb13430d1b956f83abbe21807072261993b110887d722f64889eed55214dc7" -O HeLa.tar
mkdir data
tar xvf HeLa.tar -C data --strip-components=10
echo "sample,fullpath" > samples.csv
ls -1d $PWD/data/*.d > S1
cat S1  | tr '\n' '\0' | xargs -0 -n 1 basename > S0
paste -d ','  S? >> samples.csv
cat samples.csv
wget "https://rest.uniprot.org/uniprotkb/stream?format=fasta&includeIsoform=true&query=%28%28proteome%3AUP000005640%29%29" -O human.fasta
wget "http://ftp.thegpm.org/fasta/cRAP/crap.fasta" -O crap.fasta
cat human.fasta crap.fasta >> human_crap.fasta
#wget https://raw.githubusercontent.com/animesh/scripts/master/sage.json
#sage sage.json -f human_crap.fasta --batch-size 5 *.mzML
./nextflow main.nf --max_memory '20.GB' --max_cpus 5 -profile docker --fasta human_crap.fasta --input samples.csv --outdir sage_samples
```

[DIA](https://bioshare.bioinformatics.ucdavis.edu/bioshare/view/cts8a50sb36put8/)
```
wget -r --level=10 -nH -nc --cut-dirs=3 --no-parent --reject "wget_index.html" check-certificate --header "Cookie: sessionid=None;" https://bioshare.formatics.ucdavis.edu/bioshare/wget/cts8a50sb36put8/wget_index.html
for i in 26*.zip ; do echo $i ; unzip $i ; done
```


[todo](https://github.com/sylabs/singularity/blob/main/INSTALL.md)
```
sudo snap install go --classic
go get -d github.com/sylabs/singularity
singularity run docker://godlovedc/lolcow
```
[sandbox](https://github.com/mahesh-panchal/Nextflow_sandbox)

