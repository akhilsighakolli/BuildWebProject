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
        stage("Deploy into tomcat")
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '4fd78f36-9433-4f3a-a60d-12db7a62ef20', path: '', url: 'http://3.110.117.208:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
