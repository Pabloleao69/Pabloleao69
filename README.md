  matrix:
        arch:
          - x64
          - x86
        node:
          - 10
          - 12
@@ -22,25 +21,37 @@ jobs:
          - 18
          - 20
          - 22
          - 23
        os:
          - macOS-latest
          - ubuntu-latest
          - windows-latest
        exclude:
        include:
          - arch: x86
            os: macOS-latest
            node: 10
            os: windows-latest
          - arch: x86
            node: 12
            os: windows-latest
          - arch: x86
            node: 14
            os: windows-latest
          - arch: x86
            node: 16
            os: windows-latest
          - arch: x86
            os: ubuntu-latest
            node: 20
            os: windows-latest
          - arch: x86
            node: 18
            node: 22
            os: windows-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}
          architecture: ${{ matrix.arch }}
          cache: 'npm'
          cache: npm
          cache-dependency-path: ./package.json
      - run: npm install
      - run: npm run lint
