# setup-spark ✨

[![Run setup-spark action](https://github.com/vemonet/setup-spark/workflows/Run%20setup-spark%20action/badge.svg)](https://github.com/vemonet/setup-spark/actions?query=workflow%3A%22Run+setup-spark+action%22) [![Code scanning](https://github.com/vemonet/setup-spark/workflows/CodeQL%20analysis/badge.svg)](https://github.com/vemonet/setup-spark/actions?query=workflow%3A%22CodeQL+analysis%22)

This action sets up Apache Spark in your environment for use in GitHub Actions by:

- installing and adding `spark-submit` and `spark-shell` to `PATH`
- setting `SPARK_HOME`, `PYSPARK_PYTHON` environment variable (and others) in the workflow

This enables to test applications using a local Spark context in GitHub Actions.

# Usage

See [action.yml](action.yml) for a complete rundown of the available parameters.

You will need to setup `python` and `java` in the job before setting up `spark`

Basic:
```yaml
steps:
- uses: actions/checkout@v2
- uses: actions/setup-python@v2
  with:
    python-version: '3.7'
- uses: actions/setup-java@v1
  with:
    java-version: '11'
- uses: vemonet/setup-spark@v1
  with:
    spark-version: '3.0.1' # Exact version
- run: spark-submit --version
```

# Available versions of Apache Spark

`setup-spark` has been tested for Apache Spark version `3.0.1` and for PySpark applications using Python `3.6`,  `3.7`,  `3.8`.

The Spark installation has been built based on the [jupyter/docker-stack PySpark notebook Dockerfile](https://github.com/jupyter/docker-stacks/blob/master/pyspark-notebook/Dockerfile)

The installation have only been tested on Linux (Ubuntu 18 and 20 runners)

> Feel free to test other Spark version and submit issues or pull requests!

## Developing

1. Install:

```bash
npm install
```

2. Generates js files, any files generated using `tsc` will be added to `lib/`, however those files also are not uploaded to the repository and are excluded using `.gitignore`.

```bash
tsc
```

3. Build the `index.js` file

```bash
ncc build src/setup-spark.ts
```

4. Commit and push the generated `index.js` file

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE).

# Contributions

Contributions are welcome! See our [Contributor's Guide](docs/CONTRIBUTING.md).
