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
                deploy adapters: [tomcat9(credentialsId: 'caa53acb-7435-49e0-8b95-c8f7da96aee1', path: '', url: 'http://65.1.112.153:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
