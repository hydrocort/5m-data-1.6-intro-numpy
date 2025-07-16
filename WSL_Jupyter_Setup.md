# WSL Jupyter Notebook Setup Guide

Follow these steps to set up your Jupyter Notebook environment in WSL with automatic browser launching:

---

## 1. Change the `prefix` in `environment.yml`

1. Open `environment.yml` in the `5m-data-1.6-intro-numpy` directory.
2. Find the line starting with `prefix:` at the end of the file.
3. Change it to match your WSL user's Miniconda path. For example:
   ```yaml
   prefix: /home/<your-username>/miniconda3/envs/pds
   ```
   Replace `<your-username>` with your actual WSL username (check with `echo $USER`).
4. Alternatively, you can remove the `prefix:` line to let conda use the default location.

---

## 2. Install `wslview`

1. Open a WSL terminal.
2. Run the following commands:
   ```bash
   sudo apt update
   sudo apt install wslu
   ```
3. Test that `wslview` works:
   ```bash
   wslview https://www.google.com
   ```
   This should open your default Windows browser.

---

## 3. Make the `BROWSER=wslview` Setting Permanent

1. Open your `.bashrc` file in your home directory:
   ```bash
   nano ~/.bashrc
   ```
2. Add the following lines at the end of the file:
   ```bash
   # Always use wslview to open browser from WSL
   export BROWSER=wslview
   ```
3. Save and close the file (in nano: press `Ctrl+O`, `Enter`, then `Ctrl+X`).
4. Apply the changes immediately by running:
   ```bash
   source ~/.bashrc
   ```

---

## 4. (Optional) Create the Conda Environment

1. In the `5m-data-1.6-intro-numpy` directory, run:
   ```bash
   conda env create -f environment.yml
   ```
2. Activate the environment:
   ```bash
   conda activate pds
   ```
3. Start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
   Your default Windows browser should open automatically.

---

**You are now set up to use Jupyter Notebook in WSL with automatic browser launching!** 