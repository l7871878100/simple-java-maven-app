pipeline{
    agent none
    stages{
        stage("Build"){
            agent{
                docker {
                    image 'maven:3-alpine'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps{
                sh "mvn -B -DskipTests clean package"
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("node"){
            agent{
                docker {
                    image 'node:alpine'
                }
            }
            steps{
                sh "node -v"
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