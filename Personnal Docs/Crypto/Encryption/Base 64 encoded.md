---
share: true
---
```markdown
# Note: Decoding Base64 (Multiple Layers)

## Example of Base64 Encoded String

```
Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0==
```

## How to Decode

Use the following command to decode a Base64 string:

```bash
echo "VmpGU1NtVkdTWGxTYkdScFUwWktjRlZyVmt0VE1WWnhVMjA1VG1KSGVIbFhhMXBoVlZaV1ZVMUVhejA" | base64 -d
```

## Double/Multiple Encoding

If the result still looks like random characters, it is probably encoded multiple times.  
Repeat the decoding command until you get readable text.

**Example:**  
The string above needs to be decoded **5 times** to finally reveal:  
```
rabbit hole
```

## Tips

- If the output is still unreadable, try decoding again.
- You can automate multiple decodings with a loop in bash:

```bash
echo "<your_base64_string>" | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
```

Or, for an unknown number of layers:

```bash
result="<your_base64_string>"
for i in {1..10}; do
    result=$(echo "$result" | base64 -d)
    echo "$result"
done
```

---

**Summary:**  
Base64 strings can be encoded multiple times.  
Keep decoding until you get a readable result.