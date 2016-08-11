# Interactive data displays with Jupyter notebooks - Example Notebooks

__Ioanna Ioannou__ and __Maoyuan Liu__

Forecast Systems Team

Research and Development

Bureau of Meteorology

# Installation

## Requirements

__Python__
- `pandas` - loading data
- `matplotlib`, `bokeh`, `plotly` - plotting libraries
- `ipywidgets` - provides UI widgets
- `jupyter`, `notebook` - provides the notebook environment
- `jupyter-dashboards`, `jupyter-cms` - provides dashboards layout extensions
- `jupyter-kernel-gateway` - provides kernel gateway for dashboards

__System__
- `node`, `npm` - provides server and package manager for `node.js` applications

__npm__
- `jupyter-dashboards-server`, `debug` - dashboards server front-end

## Notebook installation

Prefer installing packages using Miniconda. To download, go to http://conda.pydata.org/miniconda.html

```
# work in a new conda environment
conda create -n dashboard_example python=3
source activate dashboard_example

# install packages
conda install pandas matplotlib bokeh jupyter
# conda provides the big packages, use pip for the smaller ones that
# are not yet in conda
pip install --upgrade ipywidgets
pip install jupyter-dashboards jupyter-kernel-gateway plotly

# register notebook extensions
jupyter dashboards quick-setup --py --sys-prefix
jupyter cms quick-setup --py --sys-prefix
jupyter nbextension install --py widgetsnbextension --sys-prefix
jupyter nbextension enable --py widgetsnbextension --sys-prefix
jupyter nbextension enable --py jupyter_cms --sys-prefix
jupyter nbextension enable --py jupyter_dashboards --sys-prefix
```

## Dashboard front-end installation

If you don't have the executable `npm` and `node` in your PATH,
you may need to install it using your system package manager.
The system package that provides `node` and `npm` is known under
different names for different linux distributions. Check the
documentation for your OS.

```
# install jupyter-dashboards-server
npm install jupyter-dashboards-server
npm install debug
# add `node_modules/.bin` to your PATH
```

# Running the notebook and dashboards server

```
# go to the directory which contains the notebooks

# run the kernel gateway in the background using default settings
jupyter-kernelgateway &
# listening on port 8888

# run the notebook server
juputer notebook &
# listening on port 8889

# run the dashboard server
jupyter-dashboards-server --NOTEBOOKS_DIR=`pwd` --KERNEL_GATEWAY_URL=http://127.0.0.1:8888 &
# listening on port 3000
```

Notebooks: http://localhost:8889

Dashboards: http://localhost:3000
