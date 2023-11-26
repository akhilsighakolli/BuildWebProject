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
                deploy adapters: [tomcat9(credentialsId: 'caa53acb-7435-49e0-8b95-c8f7da96aee1', path: '', url: 'http://15.207.18.162:9000/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
