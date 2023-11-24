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
                deploy adapters: [tomcat9(credentialsId: '6f661514-e95d-437c-858e-b784d53bd54c', path: '', url: 'http://52.66.141.11:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
