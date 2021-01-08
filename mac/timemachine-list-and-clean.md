# timemachine list and clean

```text
tmutil listlocalsnapshots /System/Volumes/Data
tmutil deletelocalsnapshots /System/Volumes/Data
```

```text
function tml() {
    tmutil  listlocalsnapshots /|awk -F. '{print $4}'
}
```

