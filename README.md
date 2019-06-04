# drone-env-migration-guide

drone-server and drone-agent's environment variables are changed from v0.8 to v1 ,
but there is no official documentation about it.

* upgrade guide
  * https://docs.drone.io/releases/1.0.0-rc.1/#upgrading-important
  * https://docs.drone.io/installation/github/single-machine/ etc
* drone-server
  * 1.0
    * https://docs.drone.io/reference/server/
    * https://github.com/drone/drone/blob/v1.2.0/cmd/drone-server/config/config.go
  * 0.8
    * https://0-8-0.docs.drone.io/install-for-github/ etc
    * https://github.com/drone/drone/blob/v0.8.10/cmd/drone-server/server.go
* drone-agent
  * 1.0
    * https://docs.drone.io/reference/agent/
    * https://github.com/drone/drone/blob/v1.2.0/cmd/drone-agent/config/config.go
  * 0.8
    * https://github.com/drone/drone/blob/v0.8.10/cmd/drone-agent/main.go

v0.8 | usage | v1.0 | note
--- | --- | --- | ---
DRONE_DEBUG | enable server debug mode | [DRONE_LOGS_DEBUG](https://docs.drone.io/reference/server/drone-logs-debug/)
DRONE_SERVER_HOST,DRONE_HOST | server fully qualified url (<scheme>://<host>) | [DRONE_SERVER_HOST](https://docs.drone.io/reference/server/drone-server-host/)
DRONE_SERVER_ADDR | server address | [DRONE_SERVER_PORT](https://docs.drone.io/reference/server/drone-server-port/), [DRONE_SERVER_PROTO](https://docs.drone.io/reference/server/drone-server-proto/)
DRONE_SERVER_CERT | server ssl cert path | [DRONE_TLS_CERT](https://docs.drone.io/reference/server/drone-tls-cert/) | https://docs.drone.io/administration/server/ssl/
DRONE_SERVER_KEY | server ssl key path | [DRONE_TLS_KEY](https://docs.drone.io/reference/server/drone-tls-key/) | https://docs.drone.io/administration/server/ssl/
DRONE_LETS_ENCRYPT | enable let's encrypt | [DRONE_TLS_AUTOCERT](https://docs.drone.io/reference/server/drone-tls-autocert/) | https://docs.drone.io/administration/server/ssl-with-lets-encrypt/
DRONE_QUIC | enable quic |
DRONE_WWW | serve the website from disk |
DRONE_ADMIN | list of admin users | [DRONE_USER_CREATE](https://docs.drone.io/reference/server/drone-user-create/) | https://docs.drone.io/administration/user/admins/
DRONE_ORGS | list of approved organizations | [DRONE_USER_FILTER](https://docs.drone.io/reference/server/drone-user-filter/) | https://discourse.drone.io/t/drone-orgs-is-not-used-in-drone-v1-0/3963
DRONE_OPEN | enable open user registration | |
DRONE_REPO_CONFIG | file path for the drone config |
DRONE_SESSION_EXPIRES | session expiration time |
DRONE_ESCALATE | images to run in privileged mode | [DRONE_RUNNER_PRIVILEGED_IMAGES](https://docs.drone.io/reference/agent/drone-runner-privileged-images/)
DRONE_VOLUME |  |
DRONE_NETWORK |  |
DRONE_AGENT_SECRET,DRONE_SECRET | server-agent shared password | [DRONE_RPC_SECRET](https://docs.drone.io/reference/server/drone-rpc-secret/)
DRONE_SECRET_ENDPOINT | secret plugin endpoint | | https://docs.drone.io/extend/secrets/
DRONE_REGISTRY_ENDPOINT | registry plugin endpoint | |
DRONE_GATEKEEPER_ENDPOINT | gated build endpoint | |
DRONE_DATABASE_DRIVER,DATABASE_DRIVER | database driver | [DRONE_DATABASE_DRIVER](https://docs.drone.io/reference/server/drone-database-driver/)
DRONE_DATABASE_DATASOURCE,DATABASE_CONFIG | database driver configuration string | [DRONE_DATABASE_DATASOURCE](https://docs.drone.io/reference/server/drone-database-datasource/)
DRONE_PROMETHEUS_AUTH_TOKEN | token to secure prometheus metrics endpoint |
DRONE_LIMIT_MEM_SWAP | maximum swappable memory allowed in bytes | DRONE_LIMIT_MEM_SWAP
DRONE_LIMIT_MEM | maximum memory allowed in bytes | DRONE_LIMIT_MEM
DRONE_LIMIT_SHM_SIZE | docker compose /dev/shm allowed in bytes | DRONE_LIMIT_SHM_SIZE
DRONE_LIMIT_CPU_QUOTA | impose a cpu quota | DRONE_LIMIT_CPU_QUOTA
DRONE_LIMIT_CPU_SHARES | change the cpu shares | DRONE_LIMIT_CPU_SHARES
DRONE_LIMIT_CPU_SET | set the cpus allowed to execute containers | DRONE_LIMIT_CPU_SET
DRONE_GITHUB | github driver is enabled |
DRONE_GITHUB_URL | github server address | [DRONE_GITHUB_SERVER](https://docs.drone.io/reference/server/drone-github-server/)
DRONE_GITHUB_CONTEXT | github status context |
DRONE_GITHUB_CLIENT | github oauth2 client id | [DRONE_GITHUB_CLIENT_ID](https://docs.drone.io/reference/server/drone-github-client-id/)
DRONE_GITHUB_SECRET | github oauth2 client secret | [DRONE_GITHUB_CLIENT_SECRET](https://docs.drone.io/reference/server/drone-github-client-secret/)
DRONE_GITHUB_SCOPE | github oauth scope | [DRONE_GITHUB_SCOPE](https://docs.drone.io/reference/server/drone-github-scope/)
DRONE_GITHUB_GIT_USERNAME | github machine user username |
DRONE_GITHUB_GIT_PASSWORD | github machine user password |
DRONE_GITHUB_MERGE_REF | github pull requests use merge ref |
DRONE_GITHUB_PRIVATE_MODE | github is running in private mode |
DRONE_GITHUB_SKIP_VERIFY | github skip ssl verification |
DRONE_GOGS | gogs driver is enabled |
DRONE_GOGS_URL | gogs server address | [DRONE_GOGS_SERVER](https://docs.drone.io/reference/server/drone-gogs-server/)
DRONE_GOGS_GIT_USERNAME | gogs service account username |
DRONE_GOGS_GIT_PASSWORD | gogs service account password |
DRONE_GOGS_PRIVATE_MODE | gogs private mode enabled |
DRONE_GOGS_SKIP_VERIFY | gogs skip ssl verification |
DRONE_GITEA | gitea driver is enabled |
DRONE_GITEA_URL | gitea server address |
DRONE_GITEA_CONTEXT | gitea status context |
DRONE_GITEA_GIT_USERNAME | gitea service account username |
DRONE_GITEA_GIT_PASSWORD | gitea service account password |
DRONE_GITEA_PRIVATE_MODE | gitea private mode enabled |
DRONE_GITEA_SKIP_VERIFY | gitea skip ssl verification |
DRONE_BITBUCKET | bitbucket driver is enabled |
DRONE_BITBUCKET_CLIENT | bitbucket oauth2 client id | [DRONE_BITBUCKET_CLIENT_ID](https://docs.drone.io/reference/server/drone-bitbucket-client-id/)
DRONE_BITBUCKET_SECRET | bitbucket oauth2 client secret | [DRONE_BITBUCKET_CLIENT_SECRET](https://docs.drone.io/reference/server/drone-bitbucket-client-secret/)
DRONE_GITLAB | gitlab driver is enabled |
DRONE_GITLAB_URL | gitlab server address | [DRONE_GITLAB_SERVER](https://docs.drone.io/reference/server/drone-gitlab-server/)
DRONE_GITLAB_CLIENT | gitlab oauth2 client id | [DRONE_GITLAB_CLIENT_ID](https://docs.drone.io/reference/server/drone-gitlab-client-id/)
DRONE_GITLAB_SECRET | gitlab oauth2 client secret | [DRONE_GITLAB_CLIENT_SECRET](https://docs.drone.io/reference/server/drone-gitlab-client-secret/)
DRONE_GITLAB_GIT_USERNAME | gitlab service account username |
DRONE_GITLAB_GIT_PASSWORD | gitlab service account password |
DRONE_GITLAB_SKIP_VERIFY | gitlab skip ssl verification | [DRONE_GITLAB_SKIP_VERIFY](https://docs.drone.io/reference/server/drone-gitlab-skip-verify/)
DRONE_GITLAB_PRIVATE_MODE | gitlab is running in private mode |
DRONE_GITLAB_V3_API | gitlab is running the v3 api |
DRONE_STASH | stash driver is enabled |
DRONE_STASH_URL | stash server address | [DRONE_STASH_SERVER](https://docs.drone.io/reference/server/drone-stash-server/)
DRONE_STASH_CONSUMER_KEY | stash oauth1 consumer key | 
DRONE_STASH_CONSUMER_RSA | stash oauth1 private key file |
DRONE_STASH_CONSUMER_RSA_STRING | stash oauth1 private key string |
DRONE_STASH_GIT_USERNAME | stash service account username |
DRONE_STASH_GIT_PASSWORD | stash service account password |
DRONE_STASH_SKIP_VERIFY | stash skip ssl verification | [DRONE_STASH_SKIP_VERIFY](https://docs.drone.io/reference/server/drone-stash-skip-verify/)
DRONE_CODING | coding driver is enabled |
DRONE_CODING_URL | coding server address |
DRONE_CODING_CLIENT | coding oauth2 client id |
DRONE_CODING_SECRET | coding oauth2 client secret |
DRONE_CODING_SCOPE | coding oauth scope |
DRONE_CODING_GIT_MACHINE | coding machine name |
DRONE_CODING_GIT_USERNAME | coding machine user username |
DRONE_CODING_GIT_PASSWORD | coding machine user password |
DRONE_CODING_SKIP_VERIFY | coding skip ssl verification |
DRONE_KEEPALIVE_MIN_TIME | server-side enforcement policy on the minimum amount of time a client should wait before sending a keepalive ping. |
