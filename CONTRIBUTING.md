# Contributing to dsviper-components-qml

Thanks for your interest in contributing.

## Reporting issues

Use [GitHub Issues](https://github.com/digital-substrate/dsviper-components-qml/issues) and pick the appropriate template (bug report or feature request).

## Submitting pull requests

1. Fork the repository and create a feature branch from `main`
2. Make your changes
3. Verify a downstream consumer still imports cleanly — typically by running `cdbe`, `dbe` (from [`dsviper-tools-qml`](https://github.com/digital-substrate/dsviper-tools-qml)) or `graph_editor` (from [`ge-qml`](https://github.com/digital-substrate/ge-qml)) against your local checkout
4. Open a pull request with a clear description of what changed and why

## Running locally

Requires Python 3.14+ and PySide6 with QML support.

```bash
pip install -r requirements.txt          # PySide6 and deps
pip install dsviper                      # Viper Python binding
```

This repo is a library — there is no entry point. Consumers vendor `dsviper_components_qml/` in-tree (synced via their own `dev/sync_dsviper_components_qml.py`).

## Architecture

`dsviper_components_qml/` is a Python package exposing:

- Python models (controllers, managers, notifiers) bridged to QML via `Property`/`Slot` decorators and camelCase signals
- QML components under `dsviper_components_qml/qml/` (with a `qmldir` module declaration)
- `register_qml_types()` for QML-importable type registration

## License

This project is licensed under the MIT License (see [LICENSE](LICENSE)). By submitting a pull request, you agree that your contribution is provided under the same license (inbound = outbound). No CLA is required.
