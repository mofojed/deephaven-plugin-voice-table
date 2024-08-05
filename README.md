# deephaven-plugin-voice-table

This is a Python plugin for Deephaven generated from a [deephaven-plugin](https://github.com/deephaven/deephaven-plugins) template.

Specifically, this plugin is a bidirectional widget plugin, which can send and receive messages on both the client and server.
The plugin works out of the box, demonstrates basic plugin structure, and can be used as a starting point for building more complex plugins.

## Plugin Structure

The `src` directory contains the Python and JavaScript code for the plugin.
Within the `src` directory, the deephaven_plugin_voice_table directory contains the Python code.

Additionally, the `test` directory contains Python tests for the plugin. This demonstrates how the embedded Deephaven server can be used in tests.
It's recommended to use `tox` to run the tests, and the `tox.ini` file is included in the project.

## Building the Plugin

To build the plugin, you will need `python` installed, as well as the `build` package for Python.
The python venv can be created and the recommended packages installed with the following commands:

```sh
cd deephaven_plugin_voice_table
python -m venv .venv
source .venv/bin/activate
pip install --upgrade -r requirements.txt
```

Then, build the Python plugin from the top-level directory:

```sh
python -m build --wheel
```

The built wheel file will be located in the `dist` directory.

## Installing the Plugin

The plugin can be installed into a Deephaven instance with `pip install <wheel file>`.
The wheel file is stored in the `dist` directory after building the plugin.
Exactly how this is done will depend on how you are running Deephaven.
If using the venv created above, the plugin and server can be created with the following commands:

```sh
pip install deephaven-server
pip install dist/deephaven_plugin_voice_table-0.0.1.dev0-py3-none-any.whl
deephaven server
```

See the [plug-in documentation](https://deephaven.io/core/docs/how-to-guides/use-plugins/) for more information.

## Using the Plugin

Once the Deephaven server is running, the plugin should be available to use.

<!-- TODO: Fill in how to use -->

## Distributing the Plugin

To distribute the plugin, you can upload the wheel file to a package repository, such as [PyPI](https://pypi.org/).
The version of the plugin can be updated in the `setup.cfg` file.

There is a separate instance of PyPI for testing purposes.
Start by creating an account at [TestPyPI](https://test.pypi.org/account/register/).
Then, get an API token from [account management](https://test.pypi.org/manage/account/#api-tokens), setting the “Scope” to “Entire account”.

To upload to the test instance, use the following commands:

```sh
python -m pip install --upgrade twine
python -m twine upload --repository testpypi dist/*
```

Now, you can install the plugin from the test instance. The extra index is needed to find dependencies:

```sh
pip install --index-url https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple/ deephaven-plugin-voice-table
```

For a production release, create an account at [PyPI](https://pypi.org/account/register/).
Then, get an API token from [account management](https://pypi.org/manage/account/#api-tokens), setting the “Scope” to “Entire account”.

To upload to the production instance, use the following commands.
Note that `--repository` is the production instance by default, so it can be omitted:

```sh
python -m pip install --upgrade twine
python -m twine upload dist/*
```

Now, you can install the plugin from the production instance:

```sh
pip install deephaven-plugin-voice-table
```

See the [Python packaging documentation](https://packaging.python.org/en/latest/tutorials/packaging-projects/#uploading-the-distribution-archives) for more information.
