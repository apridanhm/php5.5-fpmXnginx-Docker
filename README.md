# PHP Legacy (PHP 5.5) Dockerized Environment

This repository provides a **containerized environment for running legacy PHP (PHP 5.5) applications**
on **modern operating systems** using Docker and Docker Compose.

The goal of this project is **not to modernize the application code**, but to:
- preserve legacy systems
- isolate deprecated runtime dependencies
- allow legacy PHP apps to run safely on up-to-date hosts

This setup reflects real-world scenarios commonly found in universities,
enterprises, and long-running internal systems.

---

## Why This Exists

Many organizations still rely on **legacy PHP applications** that:
- cannot be easily upgraded
- depend on deprecated PHP versions
- must remain operational for business or academic reasons

Running PHP 5.5 directly on modern Linux distributions is no longer supported.
Docker provides a clean and secure way to **decouple legacy runtime from the host OS**.

---

## Architecture Overview

- **Nginx** handles HTTP requests
- **PHP-FPM 5.5** runs inside an isolated container
- Host OS remains modern and clean
- No legacy packages installed on the host


Client
|
v
Nginx (Container)
|
v
PHP-FPM 5.5 (Container)



---

## Tech Stack

- PHP 5.5 (legacy runtime)
- PHP-FPM
- Nginx
- Docker
- Docker Compose

---

## How to Run

Run the following commands from the directory containing `docker-compose.yml`:

```bash
docker compose build --no-cache
docker compose up -d

