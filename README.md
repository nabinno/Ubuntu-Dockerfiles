# Ubuntu Dockerfiles

This repository provides Dockerfiles for use with Ubuntu. Popular
implementations here will be published to the Ubuntu namespace in the
docker index.

## Contribution Guidelines

Each Dockerfile should contain a README that includes the following:

* Version of Ubuntu and Docker that it was built/tested against
* Instructions for building the Docker image

```
    For example: docker build --rm=true -t my/image .
```

* Instructions for running the image, including examples for
  persistent data, port mapping, etc.
* Examples for testing and/or validating the functionality of the
  image.
* Do not include executable scripts. Provide them and mark them as
  executable in the Dockerfile

```
    ADD ./script.sh /usr/bin/
    RUN chmod -v +x /usr/bin/script.sh
```

* If creating a container for a specific language, specify the version
  of that language.
* If yum is used during the build process, run a clean afterwards to
  reduce the image size.

---

## EPILOGUE
>     A whale!
>     Down it goes, and more, and more
>     Up goes its tail!
>
>     -Buson Yosa
