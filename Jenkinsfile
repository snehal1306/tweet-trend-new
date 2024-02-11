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
                 echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                 echo "----------- build complted ----------"
            }
        }
        stage("sonarQube analysi"){
	    environmnet {
                scannerHome = tool 'sneh-sonar-scanner'
	    }
            steps {
                withSonarQubeEnv('ani-sonarqube-server') {
                   sh "${scannerHome}/bin/sonar-scanner"
                }
	    }
	}
    }
}
