# nano-autocolor
Simple bash script configuring nano to use default syntax highlighting.

All it does is appending include of each .nanorc file in /usr/share/nano/ to toggle syntax highlighting, so you don't have to write each include manually.

```bash
#!/bin/bash
read -p $'Do you want to overwrite ~/.nanorc ? Y/N\nWarning, you might end up with duplicate "include" or break your config otherwise.\nIf you don't have a nanorc, just ignore this.\n' -n 1
if [[ $REPLY =~ ^[Yy]$ ]]; then rm $HOME/.nanorc; fi
echo;echo
for file in /usr/share/nano/*.nanorc;
    do
        echo "include $file" >> $HOME/.nanorc;
    done
cat $HOME/.nanorc
```
