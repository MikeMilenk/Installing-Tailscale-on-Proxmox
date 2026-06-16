## Installing Tailscale on Proxmox

I’m using Tailscale because I want to access my home server remotely without opening any ports on my router.

This gives me secure remote access to Proxmox from anywhere, without port forwarding or exposing my network to the internet.

# Installing Tailscale on Proxmox

Tailscale allows secure remote access to your Proxmox server without opening firewall ports or configuring a traditional VPN.

After installation, you'll be able to access the Proxmox web interface from anywhere using your Tailscale network.

## Create a Tailscale Account

Create a free account:

[Tailscale](https://tailscale.com?utm_source=chatgpt.com)

---

## Install Tailscale

Open the Proxmox shell from the web interface or connect via SSH.

Run:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

This installs the latest stable version of Tailscale on the Proxmox host.

---

## Connect Proxmox to Your Tailnet

Start Tailscale:

```bash
tailscale up
```

The command will display a login URL.

Open the URL in your browser and log in to your Tailscale account.

Approve the new device.

Once approved, the Proxmox host will appear in your Tailscale dashboard.

---

## Verify the Connection

Check status:

```bash
tailscale status
```

Show the assigned Tailscale IP:

```bash
tailscale ip -4
```

Example output:

```text
100.x.x.x
```

---

## Access Proxmox Remotely

You can now access the Proxmox web interface from anywhere:

```text
https://100.x.x.x:8006
```

Replace the IP with your Tailscale IP address.

No port forwarding is required.

---

## Optional: Disable Key Expiry

Since this is a server that should stay online permanently, consider disabling key expiry in the Tailscale admin console.

Open:

Machines → Select your Proxmox host → Disable Key Expiry

This prevents the server from requiring periodic re-authentication.
![Disable Key Expiry](https://github.com/MikeMilenk/Installing-Tailscale-on-Proxmox/blob/5081490fd2b2fddecd50190c697b2bb77afd6e32/Disable%20Key%20Expiry.png)
