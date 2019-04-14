<p align="center"><a href="https://github.com/crazy-max/docker-dokuwiki" target="_blank"><img height="128"src="https://raw.githubusercontent.com/crazy-max/docker-dokuwiki/master/.res/docker-dokuwiki.jpg"></a></p>

<p align="center">
  <a href="https://microbadger.com/images/crazymax/dokuwiki"><img src="https://images.microbadger.com/badges/version/crazymax/dokuwiki.svg?style=flat-square" alt="Version"></a>
  <a href="https://travis-ci.com/crazy-max/docker-dokuwiki"><img src="https://img.shields.io/travis/com/crazy-max/docker-dokuwiki/master.svg?style=flat-square" alt="Build Status"></a>
  <a href="https://hub.docker.com/r/crazymax/dokuwiki/"><img src="https://img.shields.io/docker/stars/crazymax/dokuwiki.svg?style=flat-square" alt="Docker Stars"></a>
  <a href="https://hub.docker.com/r/crazymax/dokuwiki/"><img src="https://img.shields.io/docker/pulls/crazymax/dokuwiki.svg?style=flat-square" alt="Docker Pulls"></a>
  <a href="https://quay.io/repository/crazymax/dokuwiki"><img src="https://quay.io/repository/crazymax/dokuwiki/status?style=flat-square" alt="Docker Repository on Quay"></a>
  <a href="https://www.codacy.com/app/crazy-max/docker-dokuwiki"><img src="https://img.shields.io/codacy/grade/e1c3ab643f734445bf7f6ecdd44a2614.svg?style=flat-square" alt="Code Quality"></a>
  <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=USUQWRGP52U7N"><img src="https://img.shields.io/badge/donate-paypal-7057ff.svg?style=flat-square" alt="Paypal"></a>
</p>

## About

🐳 [DokuWiki](https://www.dokuwiki.org/dokuwiki) Docker image based on Alpine Linux and Nginx.<br />
If you are interested, [check out](https://hub.docker.com/r/crazymax/) my other 🐳 Docker images!

## Features

### Included

* Alpine Linux 3.9, Nginx, PHP 7.2
* Tarball authenticity checked during building process
* OPCache enabled to store precompiled script bytecode in shared memory
* Data, configuration, plugins and templates are stored in an unique folder

### From docker-compose

* [Traefik](https://github.com/containous/traefik-library-image) as reverse proxy and creation/renewal of Let's Encrypt certificates

## Docker

### Environment variables

* `TZ` : The timezone assigned to the container (default `UTC`)
* `MEMORY_LIMIT` : PHP memory limit (default `256M`)
* `UPLOAD_MAX_SIZE` : Upload max size (default `16M`)
* `OPCACHE_MEM_SIZE` : PHP OpCache memory consumption (default `128`)
* `REAL_IP_FROM` : Trusted addresses that are known to send correct replacement addresses (default `0.0.0.0/32`)
* `REAL_IP_HEADER` : Request header field whose value will be used to replace the client address (default `X-Forwarded-For`)
* `LOG_IP_VAR` : Use another variable to retrieve the remote IP address for access [log_format](http://nginx.org/en/docs/http/ngx_http_log_module.html#log_format) on Nginx. (default `remote_addr`)

### Volumes

* `/data` : Contains configuration, plugins, templates and data

### Ports

* `8000` : HTTP port

## Use this image

### Docker Compose

Docker compose is the recommended way to run this image. You can use the following [docker compose template](examples/compose/docker-compose.yml), then run the container :

```bash
touch acme.json
chmod 600 acme.json
docker-compose up -d
docker-compose logs -f
```

### Command line

You can also use the following minimal command :

```bash
docker run -d -p 8000:8000 --name dokuwiki \
  -v $(pwd)/data:/data \
  crazymax/dokuwiki:latest
```

## Upgrade

You can upgrade DokuWiki automatically through the UI, it works well. But i recommend to recreate the container whenever i push an update :

```bash
docker-compose pull
docker-compose up -d
```

## How can I help ?

All kinds of contributions are welcome :raised_hands:!<br />
The most basic way to show your support is to star :star2: the project, or to raise issues :speech_balloon:<br />
But we're not gonna lie to each other, I'd rather you buy me a beer or two :beers:!

[![Paypal](.res/paypal.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=USUQWRGP52U7N)

## License

MIT. See `LICENSE` for more details.
