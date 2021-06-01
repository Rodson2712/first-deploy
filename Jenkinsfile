pipeline {
    agent any

    stages{
        stage('Clone') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Deploy') {
            steps {
                build job: '00-deploy/99-service-deploy', parameters: [
                        string(name: "PROJECT_NAME", value: env.JOB_BASE_NAME),
                        string(name: "REPOSITORY", value: scm.getUserRemoteConfigs()[0].getUrl())
                ], wait: true
            }
        }
    }
}