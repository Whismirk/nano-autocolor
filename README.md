# nano-autocolor
Simple bash script configuring nano to use default syntax highlighting.

All it does is appending include of each .nanorc file in /usr/share/nano/ to toggle syntax highlighting, so you don't have to write each include manually.

```bash
#!/bin/bash
read -p $'Do you want to overwrite ~/.nanorc ? Y/N\nWarning, you might end up with duplicate "include" otherwise.\n' -n 1
echo;echo
if [[ $REPLY =~ ^[Yy]$ ]]; then rm $HOME/.nanorc; fi
for file in /usr/share/nano/*.nanorc;
    do
        echo "include $file" >> $HOME/.nanorc;
    done
cat $HOME/.nanorc
```
