# Remove-Windows-Password-Using-Ubuntu-Linux-18

First off, I will not guarentee this will work. It took me about 25 minutes to figure this out by reading different articles. 

#### Articles Referenced
- https://www.lifewire.com/reset-windows-password-using-linux-2202068
- https://askubuntu.com/questions/932331/filesystem-shows-dev-nvme0n1p1-instead-of-dev-sda
- https://www.howtogeek.com/howto/14369/change-or-reset-windows-password-from-a-ubuntu-live-cd/
- https://opensource.com/article/18/3/how-reset-windows-password-linux


# How To

1. Create an Ubuntu Live (USB) or Disc
2. Boot from the Ubuntu Live(USB) / DISC and load Ubuntu 18
2. Open ```Software Sources``` by searching **Software** its one of the icons that appears.
    > Yes, I know that is a vague statement. I will update this later.

3. Under the **Ubuntu Software** tab check: 
    
    - [x] ```Community-maintained Open Source software (universe)```


4. Click: ```Close```
5. When prompted click the ```Reload``` button and wait as the list is downloaded

6. Open your terminal and type the command: 

    ```bash
    sudo apt-get install chntpw
    ```

7. Go through the install. Type ```Y``` for yes if requested

8. After the install, Type the command:
    ```bash
    lsblk -f
    ```

9. This will show all the current disks.
10. Locate the disk with the most space. 
11. The disks might be labelled like...

        /dev/nvme0n1        Windows
        /dev/nvme0          ...
        /dev/sda
        /dev/sda1

12. Type:
    ```bash
    sudo mkdir /mnt/windows
    ```

13. In the next command after ```/dev/``` use the name that points to ```Windows```
14. Type:
    ```bash
    sudo ntfs-3g /dev/nvme0n1 /mnt/windows -o force
    ```

15. Type:
    ```bash
    ls /mnt/windows
    ```

16. Type:
    ```bash
    cd /mnt/windows/Windows/System32/config
    ```

16. Type:
    ```bash
    chntpw -l sam
    ```

17. From the list generated. Replace the ```<username>``` with one the desired user.

16. Type:
    ```bash
    chntpw -u <username> SAM
    ```

    ```bash
    example:
        chntpw -u Administrator SAM
    ```

17. Go through the menu and adjust the system however you need too.
