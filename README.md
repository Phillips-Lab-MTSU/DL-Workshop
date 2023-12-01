# DL-Workshop
Deep Learning Workshop Materials

# Preliminaries

You will need to use either [Apptainer](https://apptainer.org/) (linux only) or [Docker](https://www.docker.com/) to run the demos below. Make sure you have a working Apptainer or Docker installation before proceeding.

# BERT and GPT Demo

# Taxonomic Classification Demo

Pull the software stack image and use it to create a JupyterLab session from which you can run the demo notebook.

If using Apptainer:
```
wget https://data.phillips-lab.org/sif/csci4850-2022-09-10-compbio-p2.sif
apptainer exec --writable-tmpfs -H ${HOME}:/home/jovyan csci4850-2022-09-10-compbio-p2.sif start-notebook.sh
```

If using Docker:
```
docker pull jlphillips/csci4850:2022-09-10
docker run -it --rm --name jlab -m 16g -p 8888:8888 --user root -e GRANT_SUDO=yes -v ${PWD}:/home/jovyan/work jlphillips/csci4850:2022-09-10
```

Open `Taxonomy Demo.ipynb` in JupyterLab and follow the instructions in the notebook.