#Jetstream2 Software Collection

Details on the Jetstream2 Software Collection will be forthcoming. At this time, we anticipate a shared disk that will be automatically mounted by instances. Researchers will then be able to use modules to load any combination of software they need, similar to how HPC systems do it.

This list will be ever evolving, but at this time, we anticipate the following software on the shared software store: (Items with a \* are available now. The rest will be coming shortly.)

* Matlab\*
* R\* / R Studio / Shiny
* Intel Compiler (Intel OneAPI)\*
* Singularity/Apptainer\*
* NVIDIA (formerly PGI) Compiler
* AOCC Compiler
* Anaconda\* *(Jupyter is available via Anaconda!)*
* Databases (e.g. Mysql, Postgresql, Mongo)
* Java
* Jupyter/JupyterLab/JupyterHub (as part of Anaconda)

Items like CUDA and the NVIDIA HPC SDK are not installed on the VMs or in the software collection. We recommend using the [NVIDIA containers](https://catalog.ngc.nvidia.com/containers){target=_blank} for GPU-related software from NVIDIA as the ecosystem can often be problematic for individual local installations. The [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/overview.html){target=_blank} is installed on all featured images.

This is still an ongoing effort so this list will almost certainly change in coming weeks and months.
{: .note}
