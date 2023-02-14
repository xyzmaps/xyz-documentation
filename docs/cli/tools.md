# XYZ Maps Tools and Integrations

You can acess the XYZ Maps API using a number of different SDKs and APIs.

## XYZ Spaces for Python

<https://github.com/heremaps/xyz-spaces-python>

This open source Python package allows to interact with your XYZ Maps Spaces and features on a given Hub using a higher level programmatic interface that wraps the RESTful API. Using this package you can:

- Create, read, list, update, share, delete spaces (also: get Space info and stats).
- Add, read, update, iterate, search, cluster (hex/quad bins), delete features.
- Search features by ID, tag, property, bbox, tile, radius, geometry.
- Access [add-on features](https://www.here.xyz/cli/datahub_add-on/) like H3 hexbin and quadbin clustering, virtual spaces, extended property search, and more.

### Installation

This package can be installed with `pip` or `conda` from various sources:

- Install with conda from the Anaconda [conda-forge channel](https://anaconda.org/conda-forge/xyzspaces):

    ```console
    conda install -c conda-forge xyzspaces
    ```

- Install from the [Python Package Index](https://pypi.org/project/xyzspaces/):

    ```console
    pip install xyzspaces
    ```

- Install from its source repository on GitHub:

    ```console
    pip install -e git+https://github.com/heremaps/xyz-spaces-python#egg=xyzspaces
    ```

### Documentation

The detailed documentation is available [here](https://xyz-spaces-python.readthedocs.io/en/latest/).

