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
                deploy adapters: [tomcat9(credentialsId: '027a3538-6370-48a1-978a-9c1de1639f0d', path: '', url: 'http://15.207.110.156:9000/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
