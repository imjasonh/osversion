# `osversion`

This repo contains a minimal library for detecting the current Windows version at runtime.

It's based on [similar code in Kubernetes](https://github.com/kubernetes/kubernetes/blob/30a21e9abdbbeb78d2b7ce59a79e46299ced2742/pkg/kubelet/winstats/version.go#L34-L76), itself seemingly based on [this StackOverflow answer](https://stackoverflow.com/questions/44363911/detect-windows-version-in-go), without requiring the large dependency on Kubernetes, and with end-to-end tests using GitHub Actions.

It has a single dependency on [`x/sys/windows/registry`](https://pkg.go.dev/golang.org/x/sys/windows/registry).

Its intended use is to be able to match OCI container image manifests with a platform value that specifies an `os.version`, so that the correct image can be selected, taking into account the Windows OS version.

If this package is used on any non-Windows OS, `osversion.Get` returns an empty string.

## Usage

```
import "github.com/imjasonh/osversion"

...
fmt.Printf("The current osversion is %q", osversion.Get())
...
```

