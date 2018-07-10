### Working with the Environment
Reference: [cloudbees](https://go.cloudbees.com/docs/cloudbees-documentation/use/automating-projects/jenkinsfile/)

Navigate to url: *http://jenkinshost/pipeline-syntax/globals#env* to see the full list of env variables accesible from the Jenkins Pipeline.

### Handling failures

Declarative pipeline supports post conditions: always, unstable, success, failure, and changed. Ex.
```
pipeline {
    agent any
    stages {...}
    post {
        always {
	  ...
        }
        failure {
            mail to: team@example.com, subject: 'The Pipeline failed :('
        }
    }
}
```
