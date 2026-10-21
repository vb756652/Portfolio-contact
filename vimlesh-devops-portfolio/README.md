# Vimlesh Kumar Pal — DevOps Portfolio

Responsive static portfolio website with a Jenkins pipeline to build a Docker image and deploy it to a Linux server over SSH.

## Run locally

Open `index.html` in a browser, or run:

```bash
python3 -m http.server 8080
```

Visit `http://localhost:8080`.

## Test with Docker

```bash
docker build -t vimlesh-portfolio:local .
docker run --rm -p 8080:80 vimlesh-portfolio:local
```

Visit `http://localhost:8080`.

## Jenkins deployment prerequisites

- Jenkins agent has Docker, SSH, rsync and the Jenkins SSH Agent plugin.
- Target Linux server has Docker installed and running.
- SSH deployment user can connect with a key and run Docker commands.
- Add a Jenkins credential of type **SSH Username with private key** with ID `portfolio-deploy-ssh`.
- Update `DEPLOY_HOST`, `DEPLOY_USER` and `DEPLOY_DIR` in `Jenkinsfile`.
- Allow inbound TCP port 80 on the server/cloud firewall. Restrict SSH (TCP 22) to trusted IPs.
- Push this project to a Git repository. In Jenkins create a Pipeline job using **Pipeline script from SCM** and point it to the repository's `Jenkinsfile`.

## Important security notes

- Never commit private keys, passwords or cloud credentials to Git.
- For production, manage the SSH host key in `known_hosts` rather than automatically accepting it.
- Configure HTTPS and a domain for a public production deployment.
- This is a learning pipeline. Add rollback and stronger health checks before production use.

## Personalize before publishing

Verify the email, GitHub and LinkedIn URLs in `index.html`. Replace example project descriptions with projects you have actually completed and add repository links. Adjust skill descriptions to reflect your real experience.
