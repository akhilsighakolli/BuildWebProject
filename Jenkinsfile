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
                deploy adapters: [tomcat9(credentialsId: '0b0c3ec0-097e-430f-9427-7d073b10a40d', path: '', url: 'http://15.207.110.156:9000/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
