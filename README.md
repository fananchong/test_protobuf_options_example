# test_protobuf_options_example

本例子演示了，制作好自定义选项后，如何使用

制作好自定义选项的例子，请参考： https://github.com/fananchong/test_protobuf_options

本例子主要定义 test.proto 文件

```protobuf
syntax = "proto3";

import "broadcast.proto";

package proto;

service Say {
    rpc Hello(Request) returns (mypack.NoReply) { option (mypack.Broadcast) = true; }
    rpc Ping(Request) returns (mypack.NoReply) { }
}

message Request {
    string name = 1;
}
```

并通过 proto_gen_test 生成 test.pb.go :

```go
// For example

type SayService interface {
	BroadcastHello(ctx context.Context) error
	Ping(ctx context.Context) error
}
```

## 如何生成 protoc

可以从 https://github.com/protocolbuffers/protobuf/releases 页面下载

比如:

- Windows
  - https://github.com/protocolbuffers/protobuf/releases/download/v3.9.1/protoc-3.9.1-win64.zip


## 如何生成 protoc-gen-test

```shell
git clone https://github.com/fananchong/test_protobuf_options
cd test_protobuf_options
build.bat
```

## 如何生成 test.pb.go

1. 拷贝 protoc 、 protoc-gen-test 到本目录或系统目录
2. 执行 g.bat
