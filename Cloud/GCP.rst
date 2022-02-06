.. _GCP:

======================================
Cloud Platform
======================================


Alternative 1
----------------

Below are the details of setting FinAI-Lab on cloud platform

- Step 1: Creating hub on any cloud platform (https://tljh.jupyter.org/en/latest/)


- Step 2: Setting https:

.. code:: ipython3

    sudo tljh-config set https.enabled true
		sudo tljh-config set https.letsencrypt.email ml.finance.book@gmail.com
		sudo tljh-config add-item https.letsencrypt.domains jhub3.finailab.com

- Step 3: Setting in the jupyterhub_config

Create the file jupyterhub-config.py under /opt/tljh/config/jupyterhub_config.d and put the following lines there.


 .. code:: ipython3

    c.Spawner.args = ['--NotebookApp.tornado_settings={"headers":{"Content-Security-Policy": "frame-ancestors * self *" }}']
		c.Spawner.default_url = '/lab'
		c.NotebookApp.tornado_settings = {
		    "headers": {
		        "Content-Security-Policy": "frame-ancestors 'self' *",
		        "Access-Control-Allow-Origin": "*",
		    }
		}
		c.JupyterHub.tornado_settings = { 'headers': { 'Content-Security-Policy': "frame-ancestors * self *"} }


-  Step 4 : Embed the jupyter lab inside the FinAILab

		.. note::

		   Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:8888/lab"



Alternative 2
----------------


Below are the details of setting FinAI-Lab on cloud platform

- Step 1: Creating hub on any cloud platform (https://tljh.jupyter.org/en/latest/)



- Step 2: Setting https:

.. code:: ipython3

    sudo tljh-config set https.enabled true
		sudo tljh-config set https.letsencrypt.email ml.finance.book@gmail.com
		sudo tljh-config add-item https.letsencrypt.domains jhub3.finailab.com

- Step 3: Create a file named jupyter_notebook_config.py in a specific location say /home/shared_config/
jupyter notebook --generate-config

		https://github.com/jupyterhub/the-littlest-jupyterhub/issues/312
		Add : 		c.NotebookApp.tornado_settings={'headers': {'Content-Security-Policy': "frame-ancestors * 'self' "}}
		change the permission of the file using the following code:
		chmod -R 755 /home/shared_config/jupyter_notebook_config.py

- Step 3: Setting in the jupyterhub_config

Create the file jupyterhub-config.py under /opt/tljh/config/jupyterhub_config.d and put the following lines there.


 .. code:: ipython3

    c.Spawner.args = [ '--config=/home/shared_config/jupyter_notebook_config.py']
    #c.Spawner.args = ['--NotebookApp.tornado_settings={"headers":{"Content-Security-Policy": "frame-ancestors * self *" }}']
		c.Spawner.default_url = '/lab'
		c.NotebookApp.tornado_settings = {
		    "headers": {
		        "Content-Security-Policy": "frame-ancestors 'self' *",
		        "Access-Control-Allow-Origin": "*",
		    }
		}
		c.JupyterHub.tornado_settings = { 'headers': { 'Content-Security-Policy': "frame-ancestors * self *"} }


-  Step 4 : Embed the jupyter lab inside the FinAILab

		.. note::

		   Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:8888/lab"
