# DL-Workshop
Deep Learning Workshop Materials

# Preliminaries

Lecture slides and other deep-learning info for these materials are [here](https://github.com/Phillips-Lab-MTSU/DL-Workshop/blob/main/2023-12-01%20Deep%20Learning%20Workshop%20-%20Amplify%20-%20WebVersion.pdf)

You will need to use either [Docker](https://www.docker.com/) or [Apptainer](https://apptainer.org/) (linux only) to run the demos below. Make sure you have a working Docker or Apptainer installation before proceeding!

Once you have a working container system, then clone the repo:
```
git clone https://github.com/Phillips-Lab-MTSU/DL-Workshop
cd DL-Workshop
```

# BERT and GPT/LLM Demo

Pull the software stack image and use it to create a Jupyterlab session from which you can run the demo notebook.

If using Docker:
```
docker pull jlphillips/csci:2024-01-09
docker run -it --rm --name jlab -m 16g -p 8888:8888 --user root -e GRANT_SUDO=yes -v ${PWD}:/home/jovyan/work jlphillips/csci:2024-01-09
```

If using Apptainer:
```
curl --remote-name https://data.phillips-lab.org/sif/csci-2024-01-09.sif
apptainer exec --writable-tmpfs -H ${HOME}:/home/jovyan csci-2024-01-09.sif start-notebook.sh
```

Open `BERT Embeddings.ipynb` and/or `LLM Inference.ipynb` and follow the instructions in the notebook(s).

# Text-to-Image and Image-to-Text Demo

Uses the same stack as the BERT/GPT demos above. However, you need to add relevant flags to ensure your GPU is accessible (and CUDA 11.8 or above is installed) to run the notebook. Should just be able to add the `--gpus all` flag to docker, but apptainer is more complicated and I use the following:
```
apptainer exec --nv --writable-tmpfs --env HF_HOME=${HOME}/hf_home -H jlab:${HOME} --env XLA_FLAGS="--xla_gpu_cuda_data_dir=/opt/conda/pkgs/cuda-toolkit" csci-2024-01-09.sif start-notebook.sh
```

Open `MultiModel Models.ipynb` in JupyterLab and follow the instructions in the notebook.

# Taxonomic Classification Demo

Pull the software stack image and use it to create a JupyterLab session from which you can run the demo notebook. (This stack is Python 2.10 and TF 2.9, older than the stack above).

If using Docker:
```
docker pull jlphillips/csci4850:2022-09-10
docker run -it --rm --name jlab -m 16g -p 8888:8888 --user root -e GRANT_SUDO=yes -v ${PWD}:/home/jovyan/work jlphillips/csci4850:2022-09-10
```

If using Apptainer:
```
curl --remote-name https://data.phillips-lab.org/sif/csci4850-2022-09-10-compbio-p2.sif
apptainer exec --writable-tmpfs -H ${HOME}:/home/jovyan csci4850-2022-09-10-compbio-p2.sif start-notebook.sh
```

Open `Taxonomy Demo.ipynb` in JupyterLab and follow the instructions in the notebook.
