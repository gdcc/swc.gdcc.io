# Research code

Code files have become a frequent addition to the research data deposited in Dataverse. Research code is typically developed by few researchers with the primary goal of obtaining results, while its reproducibility and reuse aspects are often overlooked. Because several independent studies reported issues trying to rerun research code, please consider the following guidelines if your dataset contains code.

## General guidelines 

Here are general guidelines that are applicable for all programming languages.

- If possible, use free and open-source file formats and software to make your research outputs more reusable and accessible.

- Make sure to use relative file paths instead of absolute (or full) file paths, as they can cause an execution error.

- Consider testing your code in a clean environment before sharing it, as it could help you identify missing files or dependencies.

## Capturing code dependencies

Capturing code dependencies will help other researchers recreate the necessary runtime environment. Without it, your code will not be able to run correctly (or at all). Once you create the file with these dependencies, make sure to include it in your dataset.

Many programing languages already enable you to capture the dependencies automatically. Here are a few examples:

- If you are using the conda package manager, you can export your environment with the command `conda env export > environment.yml`. 

- Python has multiple conventions for capturing its dependencies, but probably the best-known one is with the `requirements.txt` file, which is created using the command `pip freeze > requirements. txt`.

- If you are using the R programming language, create a file called `install.R`, and list all library dependencies that your code requires. This file should be executable in R to set up the environment.

- In case you are using multiple programming languages or different versions of the same language, it would be best to use a containerization technology such as Docker. Create a Dockerfile that builds your environment (make sure to specify dependency versions) and deposit it with the rest of the files.

We recommend taking a look at [Jupyter Binder's documentation](https://mybinder.readthedocs.io/en/latest/using/config_files.html#config-files) for other configuration files that capture code dependencies. 

## Code automation

Automatizing your code can immensely help code reviewers, reusers, but also a future you! Here are a few options on how to automatize your code.

- A simple way to automatize your code is using a bash script or Make. [Here is a good guide](https://the-turing-way.netlify.app/reproducible-research/make.html) on how to use the Make build automation tool.

- Consider using research workflow tools to automatize your analysis. A popular workflow tool is called Common Workflow Language, and you can find more information about it [here](https://www.commonwl.org/user_guide/).

## Result verification

Even when your code executes without errors, code reviewers or reusers might wonder how to verify if its outputs are as expected.

