# Packilog

A package manager for SystemVerilog.

## Installation

Packilog is currently distributed via [pypi](https://pypi.python.org/pypi/Packilog). Install it with `pip install packilog`. 

## Usage

Packilog does not yet offer much functionality, basic usage so far involves creating a local `packilog.json` file following the [manifest format](docs/manifest_format.md), then running `packilog`. The `-f` flag can be used to force overwrite of local files.

The `-t` flag can be used to kick off tests for the local package after handling dependencies, `-T` can be used to override the package default or auto-discovered test runner.
