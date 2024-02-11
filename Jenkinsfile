pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy -Dmaven.test.skip=true'
            }
        }
        stage("test") {
            steps{
                echo "--------unit test started--------"
                sh 'mvn surefire-report:report'
                echo "-----------unit test completed-------"
            }
        }

        stage('SonarQube analysis'){
            environment{
                scannerHome = tool 'sneh-sonar-scanner'
            }
            steps{
                script{
                    withSonarQubeEnv('sneh-sonarqube-server'){
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
}
}
