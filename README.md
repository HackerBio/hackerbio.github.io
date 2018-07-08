![](https://hacker.bio/assets/images/logo-small.png)

# Hacker Bio Website

An exploration into the daily lives of Software Developers, Hardware Tinkerers, Engineers and Technologists to better understand the culture, mindset and motivation of this generation.

Watch the most recent episodes at: [hacker.bio](https://hacker.bio)

## Local Development

To run locally, start by generating an SSL certificate for local usage:

```bash
cd ssl
openssl genrsa -out root.key 2048
openssl req -x509 -new -nodes -days 3650 -config openssl.cnf -key root.key -out root.pem
openssl req -new -nodes -newkey rsa:2048 -config openssl.cnf -keyout localhost.key -out localhost.csr
openssl x509 -req -in localhost.csr -CA root.pem -CAkey root.key -CAcreateserial -out localhost.crt -days 3650 -sha256 -extfile v3.ext
```

#### Add cert to the browser

```plain
Chrome -> Setting -> (Advanced) Manage Certificates -> Import -> 'root.pem'
```

### Run with `Docker Compose`

```bash
docker-compose up
```

## Video Editing Commands

###### Convert mp4 to mp3

```bash
ffmpeg -i source.mp4 -q:a 0 -map a source.mp3
```

###### look up mp3 file duration

```bash
ffmpeg -i audio.mp3 2>&1 | grep Duration
```
