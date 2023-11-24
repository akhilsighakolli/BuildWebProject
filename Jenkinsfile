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
                deploy adapters: [tomcat9(credentialsId: '315e0a0c-8d11-4965-9718-1e5a054ada65', path: '', url: 'http://65.0.11.197:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
