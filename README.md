# docker-apache2-utils

Alpine-based image with apache2-utils package

The main purpose is to provide `htpasswd` for systems the lack it in a tiny package.

## Usage

`docker run -it mhenry07/apache2-utils htpasswd <args>`

Note: on Git Bash (Windows), prepend `winpty`.
E.g. `winpty docker run -it mhenry07/apache2-utils htpasswd <args>`

For list of commands, see: <https://pkgs.alpinelinux.org/contents?name=apache2-utils&arch=x86_64&repo=main>
