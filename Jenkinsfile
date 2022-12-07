pipeline {
    agent any
    tools
        maven 'maven'

    stages {
        stage("Build") {
            steps {
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArticacts artifacts: '**/target/*.war'

                }
            }
        }

        stage("Deploy to tomcat server") {
            steps {
                deploy adapters: [tomcat8(credentialsId: '1d2f0487-e4cb-40e2-b60d-78e9bcb7fd67', path: '', url: 'http://20.244.37.36:8080/')], contextPath: 'rps', war: '**/*.war'
            }
        }
    }
}
