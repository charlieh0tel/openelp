
## Creating the build environment
```
docker build -t openelpbuild -f Dockerfile.windows .
```

## Running the build
TODO: Run cmake directly rather than cmd
```
docker run -it -v ..:c:/source openelpbuild cmd
```