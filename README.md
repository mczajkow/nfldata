# nfldata
Data Structures and Persistence Tools for NFL Data

## Pre-Requisites
To use this package, you will need to install the `openapi-generator` at: [Open API Generator](https://github.com/OpenAPITools/openapi-generator#2---getting-started). Once you have that installed, you can now generate the schema in dozens of languages (see site for what is supported).

## How-To, a Walkthrough for Python generated objects
Begin by generating Python packages using `openapi-generator` from this directory.

This uses a generator set up for eventual passing of objects via JSON over Python's Flask 

`> openapi-generator generate -g python-flask -i api/openapi.yaml -o gen/ --package-name nfldata`

This is a more general purpose Python generator in case flask was not your goal:

`> openapi-generator generate -g python -i api/openapi.yaml -o gen/ --package-name nfldata`

This will generate the entire set of schemas in Python and put them in the `gen/` folder. The objects will use a top-level package name of "nfldata".

Now go into the `gen/` directory, and explore. Depending upon which generator you used, you might see a `docs/` folder.

To generate a Python `.whl` file, simply put this line at the end of `gen/setup.py`:

`setup(name=NAME, version=VERSION, packages=find_packages())` 

and then type `python3 setup.py bdist_wheel` which will create a .whl file in dist/

If you want to just directly install the package type: `python setup.py install` which will install it to your Python environment.

Note that either of these may require elevated access to do.

## How-To, for other languages
The same command shown above will generate code in other language types if you swap out `python` for another language. Follow this link to see more [generator types](https://openapi-generator.tech/docs/generators/)