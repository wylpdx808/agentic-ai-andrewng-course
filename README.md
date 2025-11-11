### Make API keys available to Jupyter
To make API keys available to Jupyter Lab notebook, we need to create a new ipython kernel with our environment variables. 

1) In Jupyter Lab Terminal run: `jupyter kernelspec list` to see a list of installed kernels and where files are stored
2) Copy the directory that contains the kernel.json (e.g. named `python3`) to a new directory (e.g. `python3_ENV`)
3) Change the `display_name` in the new kernel.json file
4) Add an `env` dictionary with our API key(s):

    Kernel json might look like this: 
    ```
    {
    "argv": [
    "python",
    "-m",
    "ipykernel_launcher",
    "-f",
    "{connection_file}"
    ],
    "display_name": "Python 3 (ipykernel) with environment",
    "language": "python",
    "metadata": {
    "debugger": true
    },
    "env": {
        "OPENAI_API_KEY":"replace-this-with-my-openai-api-key"
    } 
    }
    ```
5) When starting a new Jupyter notebook, select `Python 3 (ipykernel) with environment` (or the kernel display name with the defined env variables)
6) In Jupyter notebook, insert `OPENAI_API_KEY = %env OPENAI_API_KEY` into one of the cells and run 