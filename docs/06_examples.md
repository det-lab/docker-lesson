# Docker in Practice
## Example 1: Local Development Environment in Seconds
**Without Docker**: A developer needs to manually install Python 3.11, PostgreSQL, and Redis, while ensuring all are compatible. Team members might be using slightly different versions, leading to issues where the program only works on some people's machines.

**With Docker**: You can instead create a `docker-compose.yml` file.
```bash
# docker-compose.yml
version: '3'
services:
  web:
    image: python:3.11
    volumes:
      - .:/app
    working_dir: /app
    command: python app.py
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: dev
      POSTGRES_PASSWORD: secret
  redis:
    image: redis:alpine
```
Now anyone can spin up the full environment with a single command:
```bash
docker compose up
```
Benefits:
* No need to install dependencies locally.
* Identical environments across all machines/
* Easy teardown and reset of dev environment.

## Example 2: Portable Web Application Deployment
**Without Docker**:
You package a Node.js app, deploy it to a virtual machine, install Node manually, manage system dependencies, worry about OS-specific bugs.
**With Docker**:
Create a `Dockerfile` for your app:
```Dockerfile
FROM node:20-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "index.js"]
```
Build and push the image to Docker Hub or your registry:
```bash
docker build -t username/my-node-app .
docker push username/my-node-app
```
Then deploy on any server (including cloud):
```bash
docker run -d -p 80:3000 username/my-node-app
```
Benefits:
* Your app runs the same everywhere: dev, staging, and production.

* No need to manage OS-level software

* One command deployment on any machine with Docker installed.


## Example 3: Testing in Clean, Disposable Environments
Want to test your app against three different versions of a database?
```bash
docker run --rm -d --name pg12 postgres:12
docker run --rm -d --name pg13 postgres:13
docker run --rm -d --name pg15 postgres:15
```
Connect your app to each one in turn to verify compatibility without needing to install anything on your machine or spin up separate VMs.

Benefits:
* Fully isolated test environments.

* No polluting your system with conflicting installs.

* Test against multiple OS or service versions quickly.

## Example 4: CI/CD Integration
In CI pipelines (GitHub Actions, GitLab CI, etc.), you can define Docker-based test environments:
```yaml
# .github/workflows/test.yml
jobs:
  test:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:15
        ports:
          - 5432:5432
    steps:
      - uses: actions/checkout@v2
      - name: Run tests in Docker
        run: docker build . && docker run my-app test
```
Benefits:

* Reliable and reproducible test environments.

* Test builds that exactly mirror production.

* Reduced setp complexity in CI scripts.
