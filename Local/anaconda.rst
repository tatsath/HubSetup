.. _anaconda:

Using local machine
===============

Run FinAILab's platform on your local machine in 3 simple steps.

-  Step 1 : pip install finailab
-  Step 2 : python -m finailab
-  Step 3 : Press "click here" button on the Finailab's set up platform screen


Alternative embedding
-----------------------------
-  Step 1 : install jupyerter lab with "pip install jupyterlab"
-  Step 2 : Download the config file here https://github.com/tatsath/finailab_install/blob/main/jupyter_notebook_config.py
-  Step 3 : Run "jupyter lab --config=<download folder>/jupyter_notebook_config.py" in anaconda
-  Step 3 : Embed the jupyter lab inside the FinAILab platform tab

.. note::

  Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:8888/lab"



More detailed embedding
-----------------------------

-  Step1 : Search for jupyter_notebook_config.py on your local machine

-  Step 2 : Add the following config in the end of jupyter_notebook_config.py :

.. code:: ipython3

    c.NotebookApp.port = 9000
    c.NotebookApp.token = ''

    ## The IP address the notebook server will listen on.
    c.NotebookApp.disable_check_xsrf = True


    c.NotebookApp.tornado_settings = {
        "headers": {
            "Content-Security-Policy": "frame-ancestors 'self' *",
    	 "Access-Control-Allow-Origin": "*",
        }
    }

-  Step 3 : Launch the jupyter lab from Anaconda
-  Step 4 : Embed the jupyter lab inside the FinAILab

.. note::

   Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:9000/lab"
