# Natural Language Processing Course Setup

This guide explains how to set up the course environment for the Natural Language Processing course.

## Recommended Tools

You can use any IDE or code editor. However using Anaconda is recommended

Download Anaconda from the official website:

https://www.anaconda.com/download

## Install Anaconda

During installation:

1. Check the option **"Add Anaconda to my PATH environment variable"** (even if it says this is not recommended).
2. Avoid installing Anaconda in a path that contains spaces.

Example:

- Avoid: `C:\Users\Your Name\...`
- Prefer: `C:\Anaconda\`

## Create the Virtual Environment

The course includes an environment file: `nlp.yaml`.

1. Create a new folder (for example: `NLP_Course`).
2. Copy `nlp.yaml` into that folder.
3. Open **Anaconda Prompt** (or **Command Prompt**, if preferred).
4. Navigate to the folder containing `nlp.yaml`:

```bash
cd path\to\your\folder
```

5. Create the environment (internet connection required):

```bash
conda env create -f nlp.yaml
```

6. Activate the environment:

```bash
conda activate nlp_course_2026
```

7. Deactivate the environment when done:

```bash
conda deactivate
```

## Understanding the Main YAML Sections

The `nlp.yaml` environment file is organized into a few main sections. Each section has a specific role:

- `name`
	Defines the environment name that Conda will create and activate.

- `channels`
	Defines where Conda should look for packages and the order of package sources.

- `dependencies`
	Defines the Conda-managed packages and versions required by the environment.

- `pip`
	Defines additional Python packages to install with pip after Conda dependencies are handled.

## Launch Jupyter Notebook

After activating the environment, run:

```bash
jupyter notebook
```

## Troubleshooting: InvalidArchiveError

In this course setup, we explicitly pin `jupyterlab_widgets` to version `3.0.15` in `nlp.yaml`.

Reason: version `3.0.16` may sometimes fail during environment creation with an error similar to:

```text
InvalidArchiveError("Error with archive ... jupyterlab_widgets-3.0.16-...")
```

This issue can be tricky to diagnose because it may look like a random Conda/network/cache problem.

If you see this error, keep the pinned version in the environment file and recreate the environment.
