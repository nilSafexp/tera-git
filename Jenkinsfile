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
                sh "mvn clean install"
                echo "========executing A========"
            }
        }
        stage("UAT"){
            steps{
                // deplo containter plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat1Details', path: '', url: 'http://192.168.0.103:8080/')], contextPath: '/app', war: '**/*.war'
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
