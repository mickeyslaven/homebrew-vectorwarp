# VectorWarp Homebrew tap

Generated from immutable main commit `aa6584fcad3a483f6442edc6568cb5e520eb4823`, with version `0.1.7` and
Homebrew revision `367`. Source SHA-256:

```
e20b50b84830e0824e458bdfd53e53b4facb4e8bb82f0bbdd83c75e2b837e04c
```

The main-branch publishing workflow builds and tests both formulas on Apple
Silicon before updating this tap. The formulas build from source; no bottles
are produced. Intel macOS remains experimental and is not qualified by the
Apple Silicon job. See the [validation limits](https://github.com/mickeyslaven/blah2-VectorWarp/blob/aa6584fcad3a483f6442edc6568cb5e520eb4823/docs/MACOS_TEST_MATRIX.md).

## Install

Install Homebrew and Xcode Command Line Tools first, then:

```sh
brew tap mickeyslaven/vectorwarp
brew install vectorwarp
vectorwarp
```

Homebrew's full name is `mickeyslaven/vectorwarp/vectorwarp` (`owner/tap/package`). Once the
tap is added, the short package names work for installation and updates.

Choose a receiver or replay in Settings, then **Save & Restart**. The app
includes the local USB Kraken companion and open UHD/HackRF adapters. The
companion fetches pinned public upstream sources; the Suite's repository-wide
redistribution terms remain unresolved, so companion bottles are not supplied.
VectorWarp never fetches, bundles, or installs the proprietary SDRplay SDK.

## Update

```sh
brew update
brew upgrade vectorwarp vectorwarp-heimdall
```

Both components build from source. Settings and recordings stay in your
application-support directory. After upgrading either component, restart a
manually started instance with `vectorwarp restart`. If you registered a
Homebrew service, use `brew services restart vectorwarp` instead.

## Everyday commands

For a manually started instance, `vectorwarp` (or `vectorwarp open`),
`vectorwarp start`, `vectorwarp stop`,
`vectorwarp restart`, `vectorwarp status`, `vectorwarp logs` and
`vectorwarp help` have the same everyday roles as on Linux. Opening the web
interface alone does not start radar processing.

The Mac launcher does not currently implement `vectorwarp version`; use
`brew list --versions vectorwarp vectorwarp-heimdall` to inspect installed
versions. Package and login-service management use Homebrew and `brew services`,
rather than Linux `apt`, `dnf` or `systemctl` commands. No `sudo` is needed for
the per-user Mac service.

## Optional login service

After configuring a receiver or replay, register the per-user service with:

```sh
brew services start vectorwarp
```

Use `brew services stop vectorwarp` to keep a supervised instance stopped,
and `brew services restart vectorwarp` to restart it. A plain `vectorwarp stop`
stops the child processes but leaves the supervisor running, so it starts them
again. `vectorwarp status` and `vectorwarp logs` work for either launch method.

## Remove

```sh
brew services stop vectorwarp
vectorwarp stop
brew uninstall vectorwarp
brew uninstall vectorwarp-heimdall
brew untap mickeyslaven/vectorwarp
```

Configuration and recordings remain in your application-support directory.
To migrate from the development `vectorwarp/local` tap, stop its service and
instance, uninstall both local formulas, and untap `vectorwarp/local` before
installing this tap. Do not rely on an upgrade to change tap ownership.
