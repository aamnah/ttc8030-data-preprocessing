```bash
# install anaconda 

conda create --name data_preprocessing

conda activate data_preprocessing

conda config --add channels conda-forge

conda install python jupyterlab pandas
```

- `-n` or `--name`

- https://jupyter.org/install
- https://conda-forge.org/docs/user/introduction.html

## JupyterLab

To run JupyterLab in a browser, run in project directory:

```bash
# jupyter notebook
jupyter lab

# http://localhost:8888/tree/exercises
```

Alternatively, use the [Jupyter VS Code extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)

```bash
# Ctrl + Shift + P
ext install ms-toolsai.jupyter
```