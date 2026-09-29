# What and Why

This repo has programs to:

- **move-duplicates**: Fast and safe duplicate file finder & mover using a 3-tier hashing algorithm.
- **doc-search**: Extract structured data from bill photos for easy search (*In Progress*).

---

## Usage

### Move Duplicates

Run `main.py` from the `move-duplicates` folder:

```bash
python3 move-duplicates/main.py -i <source_folder> -o <destination_folder> [FLAGS]
```

#### Command Arguments

| Flag | Long Option | Description |
| :--- | :--- | :--- |
| `-i` | `--source`, `--ifile` | **(Required)** Source directory to scan for duplicates. |
| `-o` | `--destination`, `--ofile` | **(Required)** Destination directory to move duplicates to. |
| `-d` | `--dry-run` | **(Optional)** Preview duplicates without moving any files. |

#### Examples

- **Dry Run (Preview Mode):**
  ```bash
  python3 move-duplicates/main.py -i /Users/akv/MyPictures -o /Users/akv/Duplicates --dry-run
  ```

- **Move Duplicates:**
  ```bash
  python3 move-duplicates/main.py -i /Users/akv/MyPictures -o /Users/akv/Duplicates
  ```

#### Features
- **3-Tier Hash Detection**: Size $\rightarrow$ Partial Hash (4KB head) $\rightarrow$ Full SHA-256 Hash for optimal performance.
- **Collision Prevention**: Automatically renames files if a filename collision exists in the destination folder.
- **Preserves Original**: Leaves 1 original file intact in the source directory.

