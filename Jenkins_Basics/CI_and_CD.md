# Continuous Integration (CI)

- automatically build and test code when changes are pushed

## Continuous Delivery/Deployment (CD)
- automatically release code after it passes tests

### Common Terminology

- Job - A task Jenkins runs
- Pipeline - Code that defines steps(written in a Jenkinsfile)
- Agent(Node) - The machine that runs jobs
- Plugin - Adds features(Git, Docker, etc.)
- Workspace - Folder where Jenkins builds our project

###  Sample Jenkinsfile

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```
