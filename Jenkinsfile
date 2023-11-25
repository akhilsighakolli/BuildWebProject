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
                deploy adapters: [tomcat9(credentialsId: 'e4d44bbd-36aa-4d9a-944e-4e9007335737', path: '', url: 'http://15.207.110.156:9000/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
