# 📚 Home Wiki

This is my personal home wiki to keep track of projects by providing guides and documentation on them. 
Feel free to use it as inspiration for your own projects or setups! 😊

## 🐳 Kubernetes Setup

I wanted to use my existing proxmox server to build a kubernetes cluster, which I named `starfleet` 🖖.
Kubernetes is basically a way to manage a collection of physical or virtual machines and distribute
workloads/services across those virtual machines by running containers. 

I used Talos Linux from Sidero Labs as the operating system. It feels very much like
working with a Kubernetes control plane, where you push configurations to Talos nodes
using the `talosctl` CLI from a remote machine being used to manage the cluster. Project
setup was super fast for these virtual machines. I just used the `talosctl` to generate
the configuration files, stood up the vms, and then pushed those configs with `talosctl`.

As soon as the node receives its config file it is ready to use with `kubectl`. 
A set of certificates will be generated that are used to authenticate to your talos 
management api (`talosctl` just calls an api served by Talos). I perform the initial 
configuration with the master node, and then for the worker nodes you just push the 
same `worker.yaml` configuration and the nodes connect to the master (control plane)
automatically and become ready to accept work.

Be sure to check out the section on adding the Talos project to your `~/.talos` folder,
that way you can run `talosctl` anywhere, even outside of the folder containing your 
talos project files. I call it a *"project"* here, but there's likely a better term
for this like *"talos configuration"* or something.

[👓 You can read that guide here!](./talos-setup/Getting-Started.md)