---
description: WSL-2
---

# Setting up development environment for chromium on Windows(WSL)

While you can mostly get away with using [chromium documentation](https://chromium.googlesource.com/chromium/src/+/main/docs/linux/build\_instructions.md), there were couple of things I had to do. So, this notes is to document them.

### Step by step Instructions

1. Clone the `depot_tools` repository

```shell-session
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
```

2. Add `depot_tools` to the PATH permanently

```shell-session
$ vi ~/.bashrc
$ echo 'export PATH="$PATH:{INSERT_FULL_PATH_TO_DEPOT_TOOLS}"' >> ~/.bashrc
```

3. Once you added `depot_tools` folder to PATH, you should be able to run the following command without issues.  Although, it might take easily an hour or so. And, it will download more than 10GB+ data

#### <mark style="color:red;">Note</mark>: If you want to clone the source code to a specific folder, you should change into that directory and then run the following command

```
$ fetch --nohooks chromium
```

4. You should now see a folder named `src`. change directory into the `src` folder and run the following command

```shell-session
$ ./build/install-build-deps.sh
```

5. If the above command failed to run or stuck with a message related to \`connecting to snap store, follow these steps
   1. edit ./etc/wsl.conf file and add the following lines. You might need to use \`sudo\`\
      `[boot]`\
      `systemd=true`
   2. exit WSL terminal
   3. run `wsl --update`
   4. open a new wsl terminal and follow step-4 again
6. run the following command to download additional binaries and other things needed

```
$ gclient runhooks
```

7. run the following command to set-up the build

```
$ gn gen out/Default
```

8. To build Chrome, run the following command

```
$ autoninja -C out/Default chrome
```

9. And the final step, run the chrome

```
$ out/Default/chrome
```
