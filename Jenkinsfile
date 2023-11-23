pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Archiving Artifacts'
                    archiveArtifacts artifacts:'**/target/*.war'
                }
            }

        }
        stage("Deploy into tomcat"){
            steps{
               deploy adapters: [tomcat9(credentialsId: '3dd622a7-e6ca-4763-8b2f-ac9a56aa475a', path: '', url: 'http://3.109.203.249:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
