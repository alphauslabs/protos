This repo contains common protobuf definitions intended to be shared to other repos as a submodule. So far, the dependent repos are:

* [blueinternal](https://github.com/alphauslabs/blueinternal)
* [blueapi](https://github.com/alphauslabs/blueapi)

Since there is no build system here, correctness can only be resolved through the importer's build system. It is assumed that the importing repo can resolve the imports used. For example, [entity.proto](./entity.proto) imports `struct.proto` like so:

```protobuf
import "google/protobuf/struct.proto";
```

This assumes that your repo should be able to resolve `struct.proto` during compilation.

Another caveat is the `go_package` definition. As of this writing, I ([@flowerinthenight](https://github.com/flowerinthenight)) don't know of any way to unify the definition across multiple repos. For example, if imported to `blueinternal`, it needs to be defined as:

```go
import "github.com/alphauslabs/blue-internal-go/protos"
```

while in `blueapi`, it should be:

```go
import "github.com/alphauslabs/blue-sdk-go/protos"
```

Please update the build system when you figure it out. At the moment, this is handled by updating import lines using `sed`.
