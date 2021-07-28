# traefik 生成 htpasswd

```text
traefik doc:
echo $(htpasswd -nB user) | sed -e s/\\$/\\$\\$/g
```

