# Conda

## Conda - Environments

```bash
# create a new environment
conda create -n <env-name>

# To add packages while creating an environment, specify them after the environment name:
conda create -n myenvironment python numpy pandas
```

```bash
# list of all your environments:
conda info --envs
```

```
conda environments:

   base           /home/username/Anaconda3
   myenvironment   * /home/username/Anaconda3/envs/myenvironment
```

The active environment is the one with an asterisk (*).

```bash
# To deactivate an active environment
conda deactivate
```

## Conda - installaing Packages

```bash
conda install <package-name>

# manually specify the channel when installing a package
conda install conda-forge::numpy
conda install conda-forge::jupyterlab

# via environment activation
conda activate myenvironment
conda install matplotlib

# via command line option
conda install --name myenvironment matplotlib
```

## Conda Forge

[a brief intro](https://conda-forge.org/docs/user/introduction.html)

```bash
# Make sure you have conda >=4.9
conda --version
# udpate Conda to the latest version
conda update conda

# Add conda-forge as the highest priority channel.
conda config --add channels conda-forge

# Activate strict channel priority (strict will be activated by default in conda 5.0).
conda config --set channel_priority strict
```


