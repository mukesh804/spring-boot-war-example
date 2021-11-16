pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    
    stages{
        stage("Test"){
            steps{
                echo "========executing A========"
                sh "mvn test"
                slackSend channel: 'jenkins', message: 'Job Started'
            }
        }

        stage("Build"){
            steps{
                 sh "mvn package"
                echo "========executing A========"
            }
        }

        stage("Deploy On Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Tomcat_Server', path: '', url: 'http://192.168.80.135:8080/')], contextPath: 'app', war: '**/*.war'
                echo "========executing A========"
            }
        }    

        stage("Deploy On Prod"){
            steps{
                echo "========executing Deploy On Prod========"
            }        

        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            slackSend channel: 'jenkins', message: 'Job Successfully Executed'
        }
        failure{
            echo "========pipeline execution failed========"
            slackSend channel: 'jenkins', message: 'Job Failed'
        }
    }
}
