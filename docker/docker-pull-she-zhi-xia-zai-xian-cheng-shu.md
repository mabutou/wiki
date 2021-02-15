# docker pull 设置下载线程数

```text
dockerd --max-concurrent-downloads xx
```

> #### Concurrent downloads <a id="concurrent-downloads"></a>
>
> By default the Docker daemon will pull three layers of an image at a time. If you are on a low bandwidth connection this may cause timeout issues and you may want to lower this via the `--max-concurrent-downloads` daemon option. See the [daemon documentation](https://docs.docker.com/engine/reference/commandline/dockerd/) for more details.
>
> For example uses of this command, refer to the [examples section](https://docs.docker.com/engine/reference/commandline/pull/#examples) below.

