# Exercises for Data Preprocessing [TTC8030]

- [x] [Pandas - part 1](./exercises/Exercise_1_Pandas_part_1.ipynb)
- [x] [Pandas - part 2](./exercises/Exercise_2_Pandas_part_2.ipynb)
- [x] [Rest API](./exercises/Exercise_3_Rest_API.ipynb)
- [x] [SQLite](./exercises/Exercise_4_SQLite.ipynb)
- [x] [Regex](./exercises/Exercise_5_Regex.ipynb)
- [x] [XML](./exercises/Exercise_6_XML.ipynb)
- [x] [Final Exercise](./exercises/Exercise_7_Final.ipynb)

## Jupyter Notebook shortcuts

- `ctrl` + `enter` - run cell
- `b` - new cell
- `d` twice - delete cell

See more shortcuts here: https://hantt.pages.labranet.jamk.fi/data-preprocessing/guides/02_jupyter-guide/

## Misc.

original order of running code cells is maintained, (e.g. if you move the cells around and use variables before they are defined), unlike Python where file is read top to bottom.

Use **Restart Kernel and Run All Cells** as the default option

suggested way of showing values in cells is just referencing the variable, specially when working with data frames.

for example

```
c
```

instead of 

```
print(c)
```

## Environment setup

#### Conda

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

#### JupyterLab

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