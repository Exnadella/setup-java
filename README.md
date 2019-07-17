# setup-java

This action sets up a java environment for use in actions by:

- optionally downloading and caching a version of java by version and adding to PATH. Downloads from [Azul's Zulu distribution](http://static.azul.com/zulu/bin/).
- registering problem matchers for error output

# Usage

See [action.yml](action.yml)

Basic:
```yaml
actions:
- uses: actions/setup-java@latest
  with:
    version: 9.0.4 // The JDK version to make available on the path. Use a whole version, such as 9.0.4, not a semver version
    architecture: x64 // (x64 or x86) - defaults to x64
- run: java -cp java HelloWorldApp
```

From local file:
```yaml
actions:
- uses: actions/setup-java@latest
  with:
    version: 4.0.0
    architecture: x64
    jdkFile: <path to jdkFile> // Optional - jdkFile to install java from. Useful for versions not supported by Azul
- run: java -cp java HelloWorldApp
```

Matrix Testing:
```yaml
jobs:
  build:
    strategy:
      matrix:
        java: [ 6.0.119, 9.0.4, 12.0.2 ]
    name: Java ${{ matrix.java }} sample
    actions:
      - name: Setup java
        uses: actions/setup-java@latest
        with:
          version: ${{ matrix.java }}
          architecture: x64
      - run: java -cp java HelloWorldApp
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)

# Contributions

Contributions are welcome!  See [Contributor's Guide](docs/contributors.md)