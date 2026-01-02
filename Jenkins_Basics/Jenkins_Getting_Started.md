# What is a Jenkinsfile

- A pipeline is defined in a file called Jenkinsfile
- Jenkinsfile is a text file that we place in the root directory of our source
code repository.
- Jenkins supports two syntaxes: Declarative (recommended) and Scripted.
    - Declarative (recommended): easier to read
    - Scripted: raw Groovy; powerful but more complex

- A Jenkinsfile is a text file (checked into our repo) that defines our Jenkins
CI/CD pipeline as code.
- With Jenkinsfile, we can
    - Build, test, and deploy in stages
    - Run steps on different agents (nodes, containers)
    - Set environment variables, parameters, options, and post actions

## Jenkins Pipeline

| Declarative                                                                                                           | Scripted                                   |
|:---------------------------------------------------------------------------------------------------------------------:|:------------------------------------------:|
| file starts with pipeline { ... }                                                                                     | Jenkinsfile does not start with pipeline {}|
| uses blocks like agent, stages, stage, steps, environment, options, post, when, parallel at declarative positions.    | use top-level Groovy                       |
|                                                                                                                       | rely on plain Groovy control flow          |
|                                                                                                                       | (if/else, for, try/catch) at the top level |
| occasionally have script { ... }  inside steps for custom logic                                                       | there’s no Declarative structure           |

### Very Basic Jenkinsfile - Hello CI
- On Windows agents, replace sh '...' with bat '...'
- Sample (Minimal) Jenkinsfile:

    ```groovy

    // Jenkinsfile (Declarative)
    pipeline {
      agent any   // run on any available agent

      stages {
        stage('Checkout') {
          steps {
            checkout scm   // checks out the repo this Jenkinsfile lives in
          }
        }

        stage('Build') {
          steps {
            sh 'echo Building...'
          }
        }

        stage('Test') {
          steps {
            sh 'echo Running tests...'
          }
        }
      }

      post {
        always {
          echo "Pipeline finished (success or failure)."
        }
      }
    }
    ```
