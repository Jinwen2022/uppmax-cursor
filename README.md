# uppmax-cursor
Here is a guide about how to run jupyter server link within cursor

# Running Jupyter Notebooks on Uppmax with Cursor App

This guide walks you through connecting the **Cursor app** to a **Jupyter Notebook running on Uppmax**.

---

## 🧠 Goal

Use a Jupyter server running on an Uppmax compute node as a kernel backend in the Cursor app.

---

## ✅ Step-by-Step Instructions

### 🔹 1. Start a Jupyter Server on Uppmax

1. Open **ThinLinc** and log in to Uppmax.  
2. Open a terminal and start an interactive job:

   ```bash
   interactive -A uppmax****-*-** -n 5 -t 24:00:00
   ```

3. Once on a compute node (e.g., `r1182`), run:

   ```bash
   module load python/3.11.8
   jupyter-notebook --ip 0.0.0.0 --no-browser
   ```

4. You’ll receive a URL like:

   ```
   http://r1182.uppmax.uu.se:8888/tree?token=f60c2da9e22c4492dc44383f306b2738d0266a3f7bb85cd4
   ```

---

### 🔹 2. Open Cursor App and Connect via SSH

1. Launch the **Cursor app**.
2. In the startup window, click the **rightmost button**: `Connect via SSH`.
3. Choose the **bottom option**: `Configure SSH Hosts`.

---

### 🔹 3. Create or Edit Your SSH Config File

If you don’t have an SSH config file yet:

1. Open a terminal on your **local computer**:

   ```bash
   nano ~/.ssh/config
   ```

2. Add the following:

   ```ssh
   Host uppmax
       HostName rackham.uppmax.uu.se
       User MyUserName  # Change to your own Uppmax username
   ```

3. Save and exit:

   * Press `Ctrl + O` to save
   * Press `Enter` to confirm
   * Press `Ctrl + X` to exit the editor

---

### 🔹 4. Point Cursor to Your SSH Config

1. Open Cursor settings (via gear icon or Command Palette).
2. Search for `Remote.SSH: Config File`.
3. Set the path to your SSH config file, e.g.:

   ```
   /Users/your_username/.ssh/config
   ```

---

### 🔹 5. Connect to Uppmax

1. Go back to `Connect via SSH`.
2. You should see `uppmax` in the list.
3. Click it and enter your Uppmax password in the **top search bar** when prompted.
4. Cursor opens a new window connected to Uppmax.

---

### 🔹 6. Open or Create a Working Folder

1. In Cursor, click **Open Folder**.
2. Navigate to and open your desired working directory on Uppmax.

---

### 🔹 7. Open/Create a Jupyter Notebook and Connect Kernel

1. Open or create a `.ipynb` notebook file on the remote host.

2. Click the **kernel name** in the top-right corner.

3. Select:

   ```
   Select Another Kernel → Existing Jupyter Server
   ```

4. Paste the URL from ThinLinc:

   ```
   http://r1182.uppmax.uu.se:8888/?token=f60c2da9e22c4492dc44383f306b2738d0266a3f7bb85cd4
   ```

---

### 🔹 8. Choose Python Environment

Cursor will show available Python environments.
Select the one that matches the loaded module (e.g., `Python 3 (ipykernel)` from `python/3.11.8`).

---

### 🔹 9. Verify Notebook Path

Ensure your notebook is saved in your intended working directory.
If not, move or re-save it.

---

## ✅ You’re All Set!

You are now running a Jupyter Notebook on Uppmax, connected and editable directly from **Cursor**.
```
