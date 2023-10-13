# SDK Extension for OCaml stable

This extension contains various components of the [OCaml](https://ocaml.org/) stable toolchain.

The OCaml Platform Tools, which includes the build system Dune, complete the OCaml development environment and provide a nice out of the box developer experience (dune dune-release merlin ocaml-lsp-server ocamlformat ocp-indent utop).

## Debugging

In order to use this extension in a Flatpak SDK environment you may add all provided tools in your PATH by executing first:
```
$ source /usr/lib/sdk/ocaml/enable.sh
```

## Development
To use the SDK with your favourite editor:
```
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=ocaml com.visualstudio.code
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=ocaml org.gnu.emacs
```

or just use `FLATPAK_ENABLE_SDK_EXT=*` to load every SDK available in your system:
```
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=* com.visualstudio.code
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=* org.gnu.emacs
```

When running your editor you should see something like this, i.e.:
```
$ flatpak run com.visualstudio.code
flatpak-vscode: Enabling SDK extension "ocaml"
```

## Create Flatpak OCaml applications

Several examples on how to Flatpak OCaml applications leveraging this SDK can be found [here](https://github.com/josecastillolema/flatpak-ocaml-examples).

## Install packages interactivelly

In order to interactivelly install [OCaml Package Manager (opam)](https://opam.ocaml.org/) packages in a Flatpak environmment you will need to create a switch first:
```
$ cp -r /usr/lib/sdk/ocaml/ $XDG_DATA_HOME
$ opam switch --root $XDG_DATA_HOME/ocaml create 5.1.0 
$ eval $(opam env --root=$XDG_DATA_HOME/ocaml --switch=5.1.0 --set-root --set-switch)

$ opam switch
#  switch  compiler                   description
→  5.1.0   ocaml-base-compiler.5.1.0  5.1.0

$ ocaml --version
The OCaml toplevel, version 5.1.0

$ opam install -y PKG  
```

## Source files generation

[flatpak-opam-generator](https://github.com/josecastillolema/flatpak-opam-generator) was used to generate the source files.