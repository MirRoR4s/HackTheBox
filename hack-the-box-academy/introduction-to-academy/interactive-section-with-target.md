# Interactive Section with Target

Sometimes we need to interact with live targets to make the learning process more effective and more realistic.

Like `My Workstation`, targets are also spawned on-demand.

If a section requires interaction with a `Target`, you can spawn it from the bottom of the page, in the top part of `Questions`.

Follow the steps below to complete this exercise.

1. Spawn your target!
2. Spawn `My Workstation` if you haven't done so.
3. From your workstation, open Firefox and browse to the target URL.
4. Answer the question below.

Interactive sections within the modules will have either an accompanying Docker target, a single VM, or multiple VMs, depending on the material. After spawning the target, there are a few ways you can interact with it.

***

### Docker Target

For modules that use a Docker target, the instance will take the form of `http://<ip>:<port>` after spawning, i.e. `http://157.245.40.149:30655`. Once this image spawns, you can choose to interact with it from the provided Pwnbox, your own VM, etc. Docker images will typically spawn more quickly than VMs. Click on `Click here to spawn the target system!` to spawn the target Docker image.

![image](https://academy.hackthebox.com/storage/modules/15/docker\_target1.png)

***

### VM Target

Modules that have either a Windows target, Active Directory (AD) environment, require multiple hosts, or otherwise cannot be completed using a Docker image will have an accompanying VM or set of VMs. You can click to spawn this target the same way. If the target VM requires authentication, you will be provided with credentials to authenticate via `SSH`. `WinRM`, `RDP`, etc. If you are not provided with credentials, it is safe to assume that you must attack the target from an unauthenticated standpoint unless otherwise instructed. If you choose to interact with the target via the Pwnbox, you will be automatically connected to the Academy lab VPN once the Pwnbox and target VM are spawned. Click on `Click here to spawn the target system!` to spawn the target VM.

![image](https://academy.hackthebox.com/storage/modules/15/vm\_target1.png)

Alternatively, you can choose to download a VPN key to interact with target VMs from your own attack box. Any targets with an accompanying VPN key will have a download button next to the Cheat Sheet on the right-hand side of the first exercise box.

You can see how much time your target has left directly under the IP address information. If your target expires, becomes unusable or unstable for any reason, feel free to click the orange arrows to spawn a fresh target. Each user can spawn their own dedicated targets. Any data (i.e., tools) saved to the target will be lost when the target either expires or a new target is spawned.

Let's try this out by spawning the target below!

**Questions**

Answer the question(s) below to complete this Section and earn cubes!

Target:  Target is spawning...\


Cheat Sheet+ 4  What is the proof text displayed in the Target website you browsed?
