> 28 août 2017 21:28:05

# ADB

----------------------------

## Copier en gardant les attributs

```sh
adb pull -p -a /sdcard/
```

* `-p` - Progress indication.
* `-a` - Copy all attributes.

----------------------------

## Backup/Restore TWRP backup

```sh
adb backup -f <filename> --twrp
adb restore <filename>
```

----------------------------
