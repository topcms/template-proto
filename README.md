# template-proto（纯 proto）

## 说明

- 仅维护 proto 协议定义；
- 不手写 `api/` 下的生成代码（由 buf 统一生成）；

## 相关配置文件

- `buf.yaml`
- `buf.lock`
- `../buf.gen.yaml`（项目根目录）

## 生成命令

推荐在项目根目录执行：

```bash
make api
```

等价命令：

```bash
cd proto && buf generate --template ../buf.gen.yaml
```

## 生成路径约定

- 生成结果输出到项目根目录的 `api/`；
- 不应生成到 `proto/api/`；
- `../buf.gen.yaml` 中 `out` 必须保持为 `..`，否则会落到错误目录。

## 修改 proto 后的标准流程

1. 修改 `proto/` 下协议文件；
2. 在项目根目录执行 `make api` 生成最新代码；
3. 执行 `go build ./...` 验证编译通过；
4. 提交 `proto/` 与 `api/` 的改动。

