✅ Definitive Fix (Kubernetes Official Repo via pkgs.k8s.io)
This is the correct and current approach. Just follow these exact steps:

🧹 1. Remove the old repo
bash
Copy
Edit
sudo rm /etc/apt/sources.list.d/kubernetes.list
🆕 2. Add Kubernetes’ new APT repo (version 1.28 as example)
bash
Copy
Edit
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | \
gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] \
https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /" | \
sudo tee /etc/apt/sources.list.d/kubernetes.list
🔁 Replace v1.28 with another version like v1.27 or v1.26 if needed.

🔄 3. Update packages
bash
Copy
Edit
sudo apt-get update
✅ 4. Install Kubernetes tools
bash
Copy
Edit
sudo apt-get install -y kubelet kubeadm kubectl
🔒 5. Optional: Prevent automatic upgrades
bash
Copy
Edit
sudo apt-mark hold kubelet kubeadm kubectl
This works flawlessly on Ubuntu Jammy (22.04) and even on Debian when done correctly.

Let me know if you want to script this for your other instance or install a specific version like 1.26.6 or 1.27.4. I can also help configure kubeadm init or join nodes if you’re setting up a cluster.
