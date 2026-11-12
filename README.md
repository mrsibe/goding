# goding

Headless coding agent built on the
[GOAT](https://github.com/mrsibe/goat) SDK.

This repository contains the former `coding`, `codingagent`, and `cmd/goding`
packages. It depends on `github.com/mrsibe/goat v0.4.0`.

## Build

```bash
go build -o ./bin/goding ./cmd/goding
```

## Usage

```bash
export OPENAI_API_KEY=...
export OPENAI_MODEL=deepseek-chat
export OPENAI_BASE_URL=https://api.deepseek.com

./bin/goding "解释一下这个仓库的目录结构"
```

没有消息参数且 stdin 是管道时，goding 会从 stdin 读取提示词。`--json`
每行输出一个 Agent 事件；`--no-session` 关闭 JSONL 会话持久化。

## Security

goding 不会询问写文件或执行命令的审批。文件工具限制在工作区内，但 `bash`
不受工作区限制，也不是操作系统沙箱。需要更强隔离时请在容器、虚拟机或独立用户
中运行。
