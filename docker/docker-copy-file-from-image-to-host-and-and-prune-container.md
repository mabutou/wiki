# docker copy file from image to host && prune container

```text
export CT=$(docker create --rm image_name) && docker cp $CT:/runapp/ROOT.jar ./ && docker rm $CT
```

