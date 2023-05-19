# WebGL Context Creation Error
At some point, chrome would not load any site that uses WebGL, although I could load the same sites on Firefox. The error would look something like: `Error: Error creating WebGL context with your selected attributes.`
Upon research a lot of sources hinted that it was a GPU driver issue, in that chrome was probably blacklisting the current driver.

```
chrome://gpu/
```
The above link gives info on chrome's interaction with your GPU.

```
chrome://flags/
```
The above allows you to set some flags that change chrome's behaviour. One of the solutions that was given by a user on stack overflow was to enable the **"Override software rendering list"** flag so as to enable gpu acceleration on unsupported devices.

## My solution (19th May 2023)
I changed my driver from the regular X.Org X server driver to **nvidia-driver 525**. That did not fix the issue however. On my Ubuntu system I downloaded **"Nvidia X Server Settings"** and went to **"PRIME Profiles"** where I selected the **"NVIDIA(Performance Mode)"**.

After that setting change, WebGL worked as usual. A theory that a stackoverflow user had given was that if your system had 2 GPUs then chrome could have issues. It's possible that my system considered the intel integrated GPU as an extra GPU and so by changing the setting to **"NVIDIA(Performance Mode)"**, the system primarily used my NVIDIA card instead of switching between the two GPUs.