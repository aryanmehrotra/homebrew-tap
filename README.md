# homebrew-tap

Homebrew formulae for [sbx](https://github.com/aryanmehrotra/sbx).

```sh
brew install aryanmehrotra/tap/sbx
```

Then, once per machine:

```sh
sbx serve --idle 5m &
sbx doctor
```

## What this installs

The prebuilt binary for your platform, taken from the
[sbx release](https://github.com/aryanmehrotra/sbx/releases) and verified against the
checksum that release published. Nothing is compiled: sbx is a single Go binary with no
dependencies outside the standard library, and building it here would mean downloading a Go
toolchain roughly twenty times the size of the thing being installed.

macOS and Linux, on Intel and Apple Silicon / arm64. sbx also publishes freebsd and windows
binaries, which Homebrew does not cover; take those from the release directly.

## Where the formula comes from

`Formula/sbx.rb` is generated, not hand-written:

```sh
# in a checkout of aryanmehrotra/sbx
scripts/brew-formula.sh v0.1.0 > Formula/sbx.rb
```

That script reads the checksums out of the release's own `SHA256SUMS`, so the formula can
only ever describe artefacts that were really published. Hand-copied checksums are one
distraction away from being wrong, and the failure a user sees is `SHA256 mismatch`, which
reads like tampering rather than like a typo.

Issues belong on the [main repository](https://github.com/aryanmehrotra/sbx/issues).
