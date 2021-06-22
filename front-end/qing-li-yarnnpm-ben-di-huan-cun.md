# 清理yarn/npm本地缓存

#### 查看已缓存包的列表 <a id="circle-heading-7"></a>

```text
yarn cache list
```

#### 查询cache缓存文件目录路径 <a id="circle-heading-8"></a>

```text
yarn cache dir
```

#### 清理缓存包 <a id="circle-heading-9"></a>

* **yarn 清除缓存**

```text
yarn cache clean
```

* **npm清除缓存**

```text
npm cache clean --force
```

#### 改变 yarn 的缓存路径 <a id="circle-heading-10"></a>

```text
yarn config set cache-folder <path>

// 通过指定 --cache-folder 的参数来指定缓存目录
yarn <command> --cache-folder <path>
```

