<<<<<<< HEAD
# CI/CD Demonstration Project

This is a comprehensive CI/CD demonstration project designed for graduate-level computer science students. It demonstrates CI/CD pipelines across three major platforms: GitHub Actions, GitLab CI/CD, and Jenkins.

## Project Structure

- **app.py**: Simple Flask web application
- **test_app.py**: Unit tests for the application
- **requirements.txt**: Python dependencies
- **Dockerfile**: Multi-stage build for the application
- **kubernetes/**: Kubernetes deployment manifests
- **.github/workflows/**: GitHub Actions workflow definitions
- **.gitlab-ci.yml**: GitLab CI/CD pipeline configuration
- **Jenkinsfile**: Jenkins pipeline configuration

## Application

The application is a simple Flask web service that provides:

- A root endpoint (`/`) that returns application information
- A health check endpoint (`/health`)

## CI/CD Pipeline Features

All three CI/CD implementations (GitHub, GitLab, Jenkins) follow the same general workflow:

1. **Test**: Run unit tests to verify application functionality
2. **Build**: Create a Docker image and push to a container registry
3. **Deploy**: Deploy the application to a Kubernetes cluster

## Setup Instructions

### Prerequisites

- Git
- Docker
- Kubernetes cluster (or Minikube for local development)
- Access to GitHub, GitLab, or Jenkins

### Local Development

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/cicd-demo.git
   cd cicd-demo
   ```

2. Set up a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

4. Run tests:
   ```
   python -m pytest test_app.py -v
   ```

5. Run the application:
   ```
   python app.py
   ```

6. Build and run with Docker:
   ```
   docker build -t cicd-demo:local .
   docker run -p 5000:5000 cicd-demo:local
   ```

## CI/CD Configuration

### GitHub Actions

1. Store your Kubernetes configuration as a secret named `KUBECONFIG` in your GitHub repository settings.
2. Push to the main branch to trigger the workflow.
3. The workflow will automatically:
   - Run tests
   - Build and push a Docker image to GitHub Container Registry (ghcr.io)
   - Deploy to your Kubernetes cluster

### GitLab CI/CD

1. Set up the following CI/CD variables in your GitLab project:
   - `CI_REGISTRY`: Your container registry URL
   - `CI_REGISTRY_USER`: Registry username
   - `CI_REGISTRY_PASSWORD`: Registry password
   - `KUBE_CONFIG`: Your base64-encoded kubeconfig file

2. Push to the main branch to trigger the pipeline.

### Jenkins

1. Create a Jenkins pipeline job using the included Jenkinsfile.
2. Set up the following credentials in Jenkins:
   - `docker-registry-credentials`: Credentials for your Docker registry
   - `kubeconfig`: Your Kubernetes configuration file

3. Configure the pipeline to use your Git repository.

## Container Registry Authentication

Each CI/CD tool handles registry authentication differently:

### GitHub Actions
Uses GITHUB_TOKEN to authenticate with GitHub Container Registry (ghcr.io)

### GitLab
Uses CI_REGISTRY_USER and CI_REGISTRY_PASSWORD variables

### Jenkins
Uses credentials defined in Jenkins credential store

## Runner Types

### GitHub Actions
- **Hosted runners**: Ubuntu, Windows, macOS runners provided by GitHub
- **Self-hosted runners**: Deploy your own runners for specialized environments

### GitLab
- **Shared runners**: Provided by GitLab
- **Specific runners**: Dedicated runners for your projects
- **Docker executor**: Isolates builds in containers
- **Shell executor**: Runs builds directly on the host
- **Kubernetes executor**: Runs builds in Kubernetes pods

### Jenkins
- **Traditional agents**: Persistent machines connected to Jenkins master
- **Dynamic agents**: Ephemeral agents (e.g., Docker, Kubernetes)
- **Cloud agents**: Agents provisioned on demand in cloud environments

## Deployment Strategies

This demo uses a basic deployment to Kubernetes, but you can extend it with:

- **Blue/Green Deployment**: Run two identical production environments
- **Canary Releases**: Gradually roll out changes to a subset of users
- **Rolling Updates**: Default Kubernetes deployment strategy that replaces pods one by one

## Best Practices

1. **Secrets Management**: Never store secrets in your repository
2. **Idempotent Deployments**: Ensure deployments can be run multiple times without issues
3. **Fail Fast**: Tests should run early in the pipeline
4. **Caching**: Cache dependencies to speed up builds
5. **Parallel Execution**: Run independent steps in parallel
6. **Manual Approval**: Add approval steps for production deployments

## Extending the Project

- Add static code analysis
- Implement security scanning
- Add end-to-end tests
- Configure monitoring and alerts
- Implement infrastructure as code
- Add feature flag capability

## Learning Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [Docker Documentation](https://docs.docker.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
=======
# ci-cdDemo



## Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

## Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/topics/git/add_files/#add-files-to-a-git-repository) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://gitlab.com/559120b-group/ci-cddemo.git
git branch -M main
git push -uf origin main
```

## Integrate with your tools

- [ ] [Set up project integrations](https://gitlab.com/559120b-group/ci-cddemo/-/settings/integrations)

## Collaborate with your team

- [ ] [Invite team members and collaborators](https://docs.gitlab.com/ee/user/project/members/)
- [ ] [Create a new merge request](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
- [ ] [Automatically close issues from merge requests](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically)
- [ ] [Enable merge request approvals](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/)
- [ ] [Set auto-merge](https://docs.gitlab.com/user/project/merge_requests/auto_merge/)

## Test and Deploy

Use the built-in continuous integration in GitLab.

- [ ] [Get started with GitLab CI/CD](https://docs.gitlab.com/ee/ci/quick_start/)
- [ ] [Analyze your code for known vulnerabilities with Static Application Security Testing (SAST)](https://docs.gitlab.com/ee/user/application_security/sast/)
- [ ] [Deploy to Kubernetes, Amazon EC2, or Amazon ECS using Auto Deploy](https://docs.gitlab.com/ee/topics/autodevops/requirements.html)
- [ ] [Use pull-based deployments for improved Kubernetes management](https://docs.gitlab.com/ee/user/clusters/agent/)
- [ ] [Set up protected environments](https://docs.gitlab.com/ee/ci/environments/protected_environments.html)

***

# Editing this README

When you're ready to make this README your own, just edit this file and use the handy template below (or feel free to structure it however you want - this is just a starting point!). Thanks to [makeareadme.com](https://www.makeareadme.com/) for this template.

## Suggestions for a good README

Every project is different, so consider which of these sections apply to yours. The sections used in the template are suggestions for most open source projects. Also keep in mind that while a README can be too long and detailed, too long is better than too short. If you think your README is too long, consider utilizing another form of documentation rather than cutting out information.

## Name
Choose a self-explaining name for your project.

## Description
Let people know what your project can do specifically. Provide context and add a link to any reference visitors might be unfamiliar with. A list of Features or a Background subsection can also be added here. If there are alternatives to your project, this is a good place to list differentiating factors.

## Badges
On some READMEs, you may see small images that convey metadata, such as whether or not all the tests are passing for the project. You can use Shields to add some to your README. Many services also have instructions for adding a badge.

## Visuals
Depending on what you are making, it can be a good idea to include screenshots or even a video (you'll frequently see GIFs rather than actual videos). Tools like ttygif can help, but check out Asciinema for a more sophisticated method.

## Installation
Within a particular ecosystem, there may be a common way of installing things, such as using Yarn, NuGet, or Homebrew. However, consider the possibility that whoever is reading your README is a novice and would like more guidance. Listing specific steps helps remove ambiguity and gets people to using your project as quickly as possible. If it only runs in a specific context like a particular programming language version or operating system or has dependencies that have to be installed manually, also add a Requirements subsection.

## Usage
Use examples liberally, and show the expected output if you can. It's helpful to have inline the smallest example of usage that you can demonstrate, while providing links to more sophisticated examples if they are too long to reasonably include in the README.

## Support
Tell people where they can go to for help. It can be any combination of an issue tracker, a chat room, an email address, etc.

## Roadmap
If you have ideas for releases in the future, it is a good idea to list them in the README.

## Contributing
State if you are open to contributions and what your requirements are for accepting them.

For people who want to make changes to your project, it's helpful to have some documentation on how to get started. Perhaps there is a script that they should run or some environment variables that they need to set. Make these steps explicit. These instructions could also be useful to your future self.

You can also document commands to lint the code or run tests. These steps help to ensure high code quality and reduce the likelihood that the changes inadvertently break something. Having instructions for running tests is especially helpful if it requires external setup, such as starting a Selenium server for testing in a browser.

## Authors and acknowledgment
Show your appreciation to those who have contributed to the project.

## License
For open source projects, say how it is licensed.

## Project status
If you have run out of energy or time for your project, put a note at the top of the README saying that development has slowed down or stopped completely. Someone may choose to fork your project or volunteer to step in as a maintainer or owner, allowing your project to keep going. You can also make an explicit request for maintainers.
>>>>>>> bf3fb5c91d902afda24670dc82cae52769914548
