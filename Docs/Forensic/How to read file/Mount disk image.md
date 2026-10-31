---
share: true
---
1. Create folder :
    
    ```
    mkdir nameofthefolder
    ```
    
2. Mount image with bytes (2048 × 512 = 1 048 576 bytes) :
    
    ```
    sudo mount -t vfat -o loop,ro usb.image nameofthefolder
    ```
    
3. Accédez au contenu :
    
    ```
    ls nameofthefolder
    ```
    

### Unmount after uses

```
sudo umount nameofthefolder
```