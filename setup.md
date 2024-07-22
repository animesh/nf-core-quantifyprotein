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

[test](https://nf-co.re/docs/usage/introduction#how-to-run-a-pipeline)
```
 ./nextflow run hello
```

[sandbox](https://github.com/mahesh-panchal/Nextflow_sandbox)
```
echo "sample,fullpath" > samples.csv #https://github.com/animesh/scripts/blob/master/scratch.slurm
ls -1d /mnt/z/*.d > S1
cat S1  | tr '\n' '\0' | xargs -0 -n 1 basename > S0
paste -d ','  S? >> samples.csv
cat samples.csv
wget "https://rest.uniprot.org/uniprotkb/stream?format=fasta&includeIsoform=true&query=%28%28proteome%3AUP000005640%29%29" -O human.fasta
wget "http://ftp.thegpm.org/fasta/cRAP/crap.fasta" -O crap.fasta
cat human.fasta crap.fasta >> human
#wget https://raw.githubusercontent.com/animesh/scripts/master/sage.json
#sage sage.json -f human --batch-size 4 *.mzML
nextflow main.nf --max_memory '16.GB' --max_cpus 4 -profile docker --proteome human --input samples.csv --outdir sage_samples
```

[todo](https://github.com/sylabs/singularity/blob/main/INSTALL.md)
```
sudo snap install go --classic
go get -d github.com/sylabs/singularity
singularity run docker://godlovedc/lolcow
```

