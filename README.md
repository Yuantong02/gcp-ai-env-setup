# Google Cloud GPU Instance Setup Tutorial (Beginner Friendly)

This guide walks you through the **beginner-friendly process of deploying a GPU-enabled environment on Google Cloud Platform (GCP)**. It is suitable for users setting up AI, machine learning, or data science environments.

It covers the full setup process — from creating a GPU-enabled VM instance, to installing Miniconda, to preparing a flexible workspace for any AI or ML task.

Originally designed for internal onboarding, this guide empowers newcomers to confidently launch their own GPU-backed projects in the cloud with minimal prior experience.

---

## Step 1: Create a Google Cloud VM Instance

1. Log in to your Google Cloud account and navigate to: [https://console.cloud.google.com](https://console.cloud.google.com)
2. From the left sidebar, go to **Compute Engine → VM Instances**, then click **"Create Instance."**
3. Instance settings:

- Machine configuration:
  - Name: Give your instance a clear name
  - choode the following parameters based on your purpose
- OS & Storage:
  - Select Operating system and Version
- Networking:
  - Allow HTTP/HTTPS if needed
- Click **Create**

📌 _Tip: Configuration parameters may vary depending on your task — check your framework or library requirements before proceeding._

---

## Step 2: Access VM via SSH and Install Miniconda

Once your VM is created, click **"Start"**, then click **SSH** to access the terminal.

Run the following commands to install Miniconda (a lightweight Python environment manager):

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

When prompted, press **Enter** or type `yes` to proceed. Once done, either close and reopen SSH, or type:

```bash
source ~/.bashrc
```

---

## Step 3: Set Up Your Python Environment

Create a new Python virtual environment:

```bash
conda create -n your-env-name python=3.10 -y
conda activate your-env-name
```

Then install any packages required for your task. For example, to install PyTorch with GPU support:

```bash
pip install torch==2.4.0+cu124 torchaudio==2.4.0+cu124 --extra-index-url https://download.pytorch.org/whl/cu124
```

You can replace this with other libraries as needed.

---

## Step 4: Upload Your Files

Use the **"Upload File"** option in the SSH window or transfer files via `scp`. After upload:

```bash
ls   # to check uploaded files
```

---

## Step 5: Run Your Scripts or Models

Execute your custom Python code or AI models. For example:

```bash
python my_script.py
```

Replace `my_script.py` with the actual script you uploaded.

---

## Step 6: Download Output Files

Use `pwd` to find your current path and `ls` to find the output file name:

```bash
pwd
ls
```

Click **"Download File"** in the SSH window and input the full path to your file.

---

## Notes

- You can reuse this environment by starting the instance and typing:

```bash
conda activate your-env-name
```

- This guide is designed to be **adaptable to different AI or ML workflows** by substituting your own scripts, models, or dependencies.

---

## About

This tutorial was created to help beginners quickly get started with GCP-based GPU environments and is used internally for onboarding.
