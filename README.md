This repo contains common protobuf definitions intended to be shared to other repos as a submodule. Since there is no build system here, correctness can only be resolved through the importer's build system.

Another caveat is the go package definition. As of this writing, I (@flowerinthenight) don't know of a way to unify the definition across multiple repos. For example, if imported to `blueinternal`, it needs to be defined as:

```go
import "github.com/alphauslabs/blue-internal-go/protos"
```

while in `blueapi`, it should be:

```go
import "github.com/alphauslabs/blue-sdk-go/protos"
```

Please update the build system when you figure it out.

Dependent repos:
* [blueinternal](https://github.com/alphauslabs/blueinternal)
* [blueapi](https://github.com/alphauslabs/blueapi)
