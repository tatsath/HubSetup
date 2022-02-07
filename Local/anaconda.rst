.. _anaconda:

Using local machine
===============


Alternative 1
-----------------------------

-  Step 1 : Run "jupyter lab --config=https://github.com/tatsath/finailab_install/blob/main/jupyter_notebook_config.py"
-  Step 2 : Launch the jupyter lab from Anaconda
-  Step 3 : Embed the jupyter lab inside the FinAILab

.. note::

  Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:8888/lab"



Alternative 2
-----------------------------

-  Step1 : Search for jupyter_notebook_config.py on your local machine

-  Step 2 : Add the following config in the end of jupyter_notebook_config.py :

.. code:: ipython3

    c.NotebookApp.port = 8888
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

   Open "new platform" and set up a name and the hub address. The address may be something like "http://localhost:8888/lab"
