# dpkg: warning: files list file for package 'x' missing

```text
for package in $(apt-get upgrade 2>&1 |\
                 grep "warning: files list file for package '" |\
                 grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do
    apt-get install --reinstall "$package";
done
```

```text
for package in $(apt-get upgrade 2>&1 | grep "warning: files list file for package '" | grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do apt-get install --reinstall "$package"; done
```

