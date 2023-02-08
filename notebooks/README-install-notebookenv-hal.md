conda create -p /work/scratch/eynardbg/shared/conda_envs/spark python=3.9
conda activate /work/scratch/eynardbg/shared/conda_envs/spark
conda install mamba
mamba install pyspark numpy pandas pyarrow matplotlib dask seaborn xarray jupyter-server-proxy ipython ipykernel -y
chmod -R a+rX /work/scratch/eynardbg/shared
ipython kernel install --user --name spark
