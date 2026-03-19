---
share: true
---
```markdown
# Note: Finding an SSID from a BSSID with Wigle.net

## What is a BSSID?

- **BSSID** (Basic Service Set Identifier) is the MAC address of a Wi-Fi access point.
- **SSID** (Service Set Identifier) is the name of the Wi-Fi network.

## How to Find the SSID from a BSSID

1. **Obtain the BSSID**
   - You can capture the BSSID using tools like `airodump-ng`, `Kismet`, or from Wi-Fi scans.

2. **Use Wigle.net**
   - Go to [https://wigle.net/](https://wigle.net/)
   - Enter the BSSID (MAC address) in the search bar.
   - Wigle.net will show information about the access point, including its SSID (network name), location, and other metadata (if available in their database).

## Tips

- Wigle.net is a global database of Wi-Fi networks, useful for OSINT and wireless investigations.
- If the BSSID is not found, it may not be in the Wigle database yet.
- You can also use Wigle’s map view to see the physical location of the access point.

---

**Summary:**  
You can find the SSID (Wi-Fi network name) from a BSSID (MAC address) by searching on [wigle.net](https://wigle.net/).

```