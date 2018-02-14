# docker-apache2-utils

Alpine-based image with apache2-utils package

The main purpose is to provide `htpasswd` in a tiny package (~5 MB) for systems that lack it.

## Usage

`docker run mhenry07/apache2-utils <command> <args>`

Note: this will run in non-interactive mode

### htpasswd interactive example

`docker run -it --rm mhenry07/apache2-utils htpasswd <args>`

Note: on Git Bash (Windows), prepend `winpty`.
E.g. `winpty docker run -it --rm mhenry07/apache2-utils htpasswd <args>`

For list of commands, see: <https://pkgs.alpinelinux.org/contents?name=apache2-utils&arch=x86_64&repo=main>

### docker-compose example (Windows host)

It gets tricky when using Git Bash for Windows when you want to run a docker command interactively *and* save output to file on the host. `winpty` is required to run a command interactively but it prevents stdout from working normally. Docker volumes are required to save the file generated in the container to the host, but winpty doesn't support relative paths and requires extra escaping. In this scenario, using `docker-compose` seems to work best for mapping volumes when running via winpty. The following example assumes the current directory is a descendent of the VirtualBox shared folder (the default is C:\Users):

- `git clone https://github.com/mhenry07/docker-apache2-utils`
- `cd docker-apache2-utils`
- `winpty docker-compose run utils <command> <args>`
  - e.g. `winpty docker-compose run --rm utils htpasswd -cB -C 14 .htpasswd user`
    - you will be prompted for a password (which won't be echoed)
    - the .htpasswd file will be saved to the current directory on the host
