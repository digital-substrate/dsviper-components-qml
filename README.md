# dsviper-components-qml

Shared Qt Quick / QML library for the dsviper Python ecosystem.
Provides the common Python models (controllers, managers,
notifiers) and QML components used by `dsviper-tools-qml` (cdbe,
dbe) and `ge-qml` (graph editor).

## Architectural position

Sits above the runtime layer. Consumes the public API of:

- `dsviper` (Python wheel) — runtime + binding.
- `PySide6` — Qt Quick / QML.

## Layout

```
dsviper_components_qml/         # Python package (importable as `dsviper_components_qml`)
├── *.py                    # source — Python models, controllers, managers
├── images/                 # source — PNG icons (with @2x retina variants)
├── qml/                    # source — QML components
│   ├── *.qml
│   └── qmldir              # QML module declaration
└── __init__.py             # exposes register_qml_types()
```

## Usage from a consumer

```python
# Python side
from dsviper_components_qml.commit_store_manager import CommitStoreManager
from dsviper_components_qml import register_qml_types

app = QApplication(sys.argv)
register_qml_types()                                # makes DS QML types available
engine = QQmlApplicationEngine()
engine.load(QUrl.fromLocalFile("Main.qml"))
```

```qml
// QML side
import QtQuick
import "dsviper_components_qml/qml" as DS              // or via module path

DS.CommitToolBar { ... }
```

## Conventions

- Documentation in **English**.
- Tag convention: `vMAJOR.MINOR.PATCH`.
- Branches: `main` + `LTS-X.Y` aligned with the dsviper ecosystem.

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE).

## Runtime dependency

At runtime, this project depends on the `dsviper` Python package
(distributed on PyPI), which is **proprietary** (PyPI classifier
`License :: Other/Proprietary License`). See
[https://pypi.org/project/dsviper/](https://pypi.org/project/dsviper/)
for the package's licensing posture and contact information.
