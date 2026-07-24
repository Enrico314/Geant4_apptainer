# Geant4 apptainer recipe

This repository contain the apptainer[^1] recipe to build a Geant4[^2] container.

### How to build the container

   With the following command:

  ```bash
  apptainer build <ApptainerImageOutName.sif> g4.def
  ```

   `g4.def` is the definition file available in this repo and `<ApptainerFolderOutName.sif>` is the new name of the container image.

   Alternatively, it is possible to compile in _sandbox_ mode, where it is still possible to modify the container; useful in the case of debugging and developments.

   ```bash
   apptainer build --sandbox <ApptainerFolderOutName> g4.def
   ```

   It is always possible to convert the output folder to a `.sif` file with the following command. This time, the output will be contained in the folder `<ApptainerFolderOutName>`.

   ```bash
   apptainer build <ApptainerImageOutName.sif> <ApptainerFolderOutName>
   ```

   Note: the host building the container must have a valid internet connection as it will fetch geant4 source code from the official website.

### How to run the container standalone

Once the container has been build (.sif or with sandbox mode) it is possible to execute it.

1. Run a shell inside the container:

   `apptainer shell <ApptainerImageOutName.sif>`

   A bash should appear and, if the container has been equipped with Geant, it is possible to find it in the: `/opt/` folder.

2. Alternatively, it is possible to run a bash script inside the container:

   `apptainer exec <ApptainerImage> <path_to_bash_script>`

---
Tested in `apptainer version 1.3.6-1.el8`.

[^1]: apptainer documentation available here [https://apptainer.org/](https://apptainer.org/). An extensive guide of apptainer in cluster computing infrastructure is available here [https://virgo-docs.hpc.gsi.de/](https://virgo-docs.hpc.gsi.de/).
[^2]: Geant4 available here [https://geant4.web.cern.ch/](https://geant4.web.cern.ch/)
