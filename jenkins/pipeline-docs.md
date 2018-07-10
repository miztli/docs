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

### Using multiple agents

Pipeline allows the use of multiple agents within the same _Jenkinsfile_

### Executing in parallel

By default pipeline stages and steps are synchronous, by using parrallel we can save sometime in case our stages are independent from each other

```
stage('Build') {
    /* .. snip .. */
}

stage('Test') {
    parallel linux: {
        node('linux') {
            checkout scm
            try {
                unstash 'app'
                sh 'make check'
            }
            finally {
                junit '**/target/*.xml'
            }
        }
    },
    windows: {
        node('windows') {
            /* .. snip .. */
        }
    }
}
```

