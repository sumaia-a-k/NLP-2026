# Natural Language Processing Course Setup

This guide explains how to set up the course environment for the Natural Language Processing course.

## What Is Conda?

Conda is a package and environment manager.

- It installs Python packages and tools.
- It creates isolated environments for different projects.
- It helps prevent version conflicts between projects on the same computer.

In this course, Conda is used to create a dedicated environment from `nlp.yaml`.

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

## List Available Environments

To see all Conda environments installed on your machine, run:

```bash
conda env list
```

or:

```bash
conda info --envs
```

The currently active environment is marked with `*`.

## Why It Is Better to Use a Separate Environment

Using a separate environment for this course is a good practice because:

- It avoids package conflicts between different projects.
- It keeps course dependencies isolated from your system-wide tools.
- It makes your setup reproducible for classmates, instructors, and future you.
- It is easier to debug when all required packages are in one dedicated environment.

## What Is the `base` Environment?

`base` is the default Conda environment created when Anaconda is installed.

- It contains Conda itself and core tools.
- You can use it, but it is usually better to keep it clean.
- For projects, create and activate a dedicated environment like `nlp_course_2026`.

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
