---
share: true
---
```markdown
# Note: Useful Linux Commands

## 1. Search for a File Containing a String

To find files containing a specific string (e.g., "toto"):

```bash
find . -type f -exec grep -l "toto" {} \;
```

- Searches recursively from the current directory.
- Lists files where the string "toto" is found.

## 2. Identify File Type

To determine the type of data in a file:

```bash
file <file>
```

- Displays the file type (e.g., text, binary, image, archive, etc.).
- Useful for identifying unknown files or checking file extensions.

## 3. Exit Any SSH Connection

To force exit from any SSH session (especially if it’s stuck):

- Press:  
  <kbd>~</kbd> + <kbd>.</kbd>  
  (Type this at the beginning of a new line.)

## 4. Extract a .tar.gz Archive

To decompress a `.tar.gz` file:

```bash
tar -xvf <path_to_tar_gz>
```

- Extracts the contents of the archive to the current directory.

## 5. Run an Installer from an Extracted Archive

After extracting, if the application is in a `bin` directory:

```bash
cd bin
./<installer_or_program>
```

- Change to the `bin` directory and run the installation or executable file.

## 6. Run an Installer from an Extracted Archive

To list command i am authorized to exec

```bash
sudo -l
```

---
