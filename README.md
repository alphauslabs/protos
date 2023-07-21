This repo contains common protobuf definitions intended to be shared to other repos as a submodule. Since there is no build system here, correctness can only be resolved through the importer's build system.

Dependent repos:
* [blueinternal](https://github.com/alphauslabs/blueinternal)
* [blueapi](https://github.com/alphauslabs/blueapi)

Another caveat is the `go_package` definition. As of this writing, I ([@flowerinthenight](https://github.com/flowerinthenight)) don't know of any way to unify the definition across multiple repos. For example, if imported to `blueinternal`, it needs to be defined as:

```go
import "github.com/alphauslabs/blue-internal-go/protos"
```

while in `blueapi`, it should be:

```go
import "github.com/alphauslabs/blue-sdk-go/protos"
```

Please update the build system when you figure it out. At the moment, this is handled by updating import lines using `sed`.
