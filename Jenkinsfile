pipeline{
    agent  any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
                echo "========executing A========"
            }
        }
        stage("UAT"){
            steps{
                // deplo containter plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat1Details', path: '', url: 'http://192.168.0.102:8080/')], contextPath: '/app', war: '**/*'
                echo "========executing A========"
            }
        }
        stage("Prod"){
            steps{
                // deplo containter plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat1Details', path: '', url: 'http://192.168.0.103:8080/')], contextPath: '/app', war: '**/*'
                echo "========executing A========"
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
