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
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
