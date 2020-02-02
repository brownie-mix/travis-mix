# travis-mix

This is a [Brownie](https://github.com/iamdefinitelyahuman/brownie) project template preconfigured for:

* Continuous integration with [Travis-CI](https://travis-ci.com/)
* Standardized testing environments with [tox](https://github.com/tox-dev/tox)
* Linting checks using [black](https://github.com/psf/black), [flake8](https://gitlab.com/pycqa/flake8) and [isort](https://github.com/timothycrosley/isort)
* [Pre-commit](https://pre-commit.com/) for linting hooks

**Please read this entire document carefully to ensure the proper setup of each component.**

Feel free to join us in the Brownie [Gitter channel](https://gitter.im/eth-brownie/community), or [open an issue](https://github.com/brownie-mix/travis-mix/issues) if you encounter a problem with this template.

## Installation

### Downloading the Template

First, [install Brownie](https://eth-brownie.readthedocs.io/en/latest/install.html). Then use the `bake` command to initialize a new project from this template:

```bash
brownie bake travis
```

### Creating a Virtual Environment

It is **strongly recommended** use a virtual environment with this project. This ensures that dependencies are strictly contained within your project and will not alter or affect your other development environment.

To create a new virtual environment and install the required dependencie:

```bash
python -m venv venv
source venv/bin/activate
pip install requirements.txt
```

In future sessions, activate the virtual environment with:

```bash
source venv/bin/activate
```

To learn more about `venv`, see the official [Python documentation](https://docs.python.org/3/library/venv.html).

### Configuring Pre-commit

[Pre-commit](https://pre-commit.com/) is a tool that executes linting checks each time you make a commit. It is useful for enforcing proper codestyle and preventing commits that would fail the linting build.

To install pre-commit locally:

```bash
pre-commit install
```

Once installed, the pre-commit hooks will automatically run each time you make a commit.

### Configuring Travis

[Travis-CI](https://travis-ci.com/) is a hosted continuous integration service. Travis runs your project tests each time you push a new commit or open a pull request, providing quick feedback on the outcome of each change.

In order to enable continuous integration:

1. If you don't have a Travis account, you can [sign up](https://travis-ci.com/signin) using your Github account.
2. From the Travis Dashboard, click on your profile picture in the upper right, click the green Activate button, and enable CI for your project repository.

The next time you push a commit, Travis will detect the presence of the `.travis.yml` file within your project, and your tests will be executed remotely.

Depending on the requirements of your project, you may also need to set the following environment variables:

* `GITHUB_TOKEN`: Github [personal access token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line#creating-a-token), required by [py-solc-x](https://github.com/iamdefinitelyahuman/py-solc-x) when querying installable solc versions.
* `WEB3_INFURA_PROJECT_ID`: Infura [project ID](https://eth-brownie.readthedocs.io/en/latest/nonlocal-networks.html#using-infura), required for connecting to Infura hosted nodes.

See the official [Travis CI documentation](https://docs.travis-ci.com/user/environment-variables/#defining-variables-in-repository-settings) for information on how to set environment variables.

## Running the Tests

This project uses [tox](https://tox.readthedocs.io/en/latest/) to standardize the local and remote testing environments.

To run all of your project's unit tests and perform linting checks:

```bash
tox
```

To run only the linting checks:

```bash
tox -e lint
```

## License

This project is licensed under the [MIT license](LICENSE).
