pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	stage ('Compile'){
	        steps {
			sh 'mvn compile'
                }
	}
	 stage ('Build'){
	        steps {
			sh 'mvn clean install'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }

	stage('Deployment'){ 
		steps { 
			sh 'sshpass -p 12345678 scp target/gamutkart.war staragile@172.31.15.55:/home/staragile/apache-tomcat-9.0.85/webapps/' 
		}
    	}
    }
}
