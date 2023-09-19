# go-install

This action builds and caches the binary of actions written in go.

The action adds the tool installation path (usually `$HOME/.local/actions-go/bin`) to the PATH.

It will first check whether there is a pre-built version of the tool cached.
If a the tool is not found locally, it will set-up go using [actions/setup-go](https://github.com/actions/setup-go)
and build the tool using `go install`.

# Usage

See [`action.yaml`](https://github.com/actions-go/go-install/blob/main/action.yml)

```
steps:
    - uses: './'
      with:
        module: "github.com/actions-go/build-go-action/cmd/hello@main"
```

The action accepts fine-tuning the `go-version` input used for [`setup-go`](https://github.com/actions/setup-go) and supports all its variants [semver](https://github.com/actions/setup-go#v3), [stable](https://github.com/actions/setup-go#using-stableoldstable-aliases) and the [basic](https://github.com/actions/setup-go#basic) usage.


## Inputs

The action accepts 2 inputs.

```
module:
  description: the go module to be installed
  required: true
go-version:  # id of input
  description: 'The version of Go to use'
  required: true
  default: '1.21'
```

## Outputs

The action generates two outputs.

```
install-path:
    description: "The file path in which the module has been installed"
cache-hit:
    description: "Whether the module has been installed from github cache"
```