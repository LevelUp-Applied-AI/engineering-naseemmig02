# Docker Notes — Day 9

## Docker Version:

docker version
Client:
 Version:           28.3.3
 API version:       1.51
 Go version:        go1.24.5
 Git commit:        980b856
 Built:             Fri Jul 25 11:36:03 2025
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.45.0 (203075)
 Engine:
  Version:          28.3.3
  API version:      1.51 (minimum version 1.24)
  Go version:       go1.24.5
  Git commit:       bea959c
  Built:            Fri Jul 25 11:34:00 2025
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.27
  GitCommit:        05044ec0a9a75232cad458027ca83437aae3f4da
 runc:
  Version:          1.2.5
  GitCommit:        v1.2.5-0-g59923ef
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0


## Hello World Test:

docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete
Digest: sha256:ef54e839ef541993b4e87f25e752f7cf4238fa55f017957c2eb44077083d7a6a
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine

docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 07:47:00.890 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 07:47:01.484 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:47:01.486 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:47:01.490 UTC [44] LOG:  database system was shut down at 2026-03-04 07:47:01 UTC
2026-03-04 07:47:01.494 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-04 07:47:01.582 UTC [41] LOG:  received fast shutdown request
2026-03-04 07:47:01.584 UTC [41] LOG:  aborting any active transactions
2026-03-04 07:47:01.586 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-04 07:47:01.587 UTC [42] LOG:  shutting down
2026-03-04 07:47:01.588 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 07:47:01.595 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.002 s, sync=0.001 s, total=0.009 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-04 07:47:01.598 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 07:47:01.698 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:47:01.698 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 07:47:01.698 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 07:47:01.701 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:47:01.704 UTC [55] LOG:  database system was shut down at 2026-03-04 07:47:01 UTC
2026-03-04 07:47:01.708 UTC [1] LOG:  database system is ready to accept connections


 docker stop pg-prework
pg-prework

 docker restart pg-prework
pg-prework

docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 07:47:00.890 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 07:47:01.484 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:47:01.486 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:47:01.490 UTC [44] LOG:  database system was shut down at 2026-03-04 07:47:01 UTC
2026-03-04 07:47:01.494 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-04 07:47:01.582 UTC [41] LOG:  received fast shutdown request
2026-03-04 07:47:01.584 UTC [41] LOG:  aborting any active transactions
2026-03-04 07:47:01.586 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-04 07:47:01.587 UTC [42] LOG:  shutting down
2026-03-04 07:47:01.588 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 07:47:01.595 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.002 s, sync=0.001 s, total=0.009 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-04 07:47:01.598 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 07:47:01.698 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:47:01.698 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 07:47:01.698 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 07:47:01.701 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:47:01.704 UTC [55] LOG:  database system was shut down at 2026-03-04 07:47:01 UTC
2026-03-04 07:47:01.708 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 07:49:03.722 UTC [1] LOG:  received fast shutdown request
2026-03-04 07:49:03.724 UTC [1] LOG:  aborting any active transactions
2026-03-04 07:49:03.726 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-04 07:49:03.726 UTC [53] LOG:  shutting down
2026-03-04 07:49:03.727 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 07:49:03.737 UTC [53] LOG:  checkpoint complete: wrote 43 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.003 s, sync=0.004 s, total=0.012 s; sync files=11, longest=0.002 s, average=0.001 s; distance=252 kB, estimate=252 kB
2026-03-04 07:49:03.740 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 07:49:31.363 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:49:31.363 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 07:49:31.363 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 07:49:31.367 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:49:31.372 UTC [29] LOG:  database system was shut down at 2026-03-04 07:49:03 UTC
2026-03-04 07:49:31.376 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 07:54:57.442 UTC [27] LOG:  checkpoint starting: time
2026-03-04 07:54:57.454 UTC [27] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.004 s, sync=0.002 s, total=0.013 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-04 07:56:00.536 UTC [1] LOG:  received fast shutdown request
2026-03-04 07:56:00.538 UTC [1] LOG:  aborting any active transactions
2026-03-04 07:56:00.540 UTC [1] LOG:  background worker "logical replication launcher" (PID 32) exited with exit code 1
2026-03-04 07:56:00.540 UTC [27] LOG:  shutting down
2026-03-04 07:56:00.541 UTC [27] LOG:  checkpoint starting: shutdown immediate
2026-03-04 07:56:00.545 UTC [27] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.001 s, sync=0.001 s, total=0.006 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=0 kB
2026-03-04 07:56:00.549 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 07:56:21.436 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 07:56:21.436 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 07:56:21.436 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 07:56:21.439 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 07:56:21.443 UTC [29] LOG:  database system was shut down at 2026-03-04 07:56:00 UTC
2026-03-04 07:56:21.448 UTC [1] LOG:  database system is ready to accept connections

---

### Step 11 — Commit and push

```bash