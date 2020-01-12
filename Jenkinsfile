pipeline {
    agent any

	tools {
		maven 'apache-maven-3.6.2'
	}
//
//	environment {
//		M2_INSTALL = "/home/gamut/distros/apache-maven-3.6.2/bin/mvn"
//	}

    stages {
		stage('Clone-Repo') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
	    	steps {
				sh 'mvn install -DskipTests'
			}
	    }
		stage('Unit Tests') {
			steps {
				sh 'mvn surefire:test'
			}
		}
		stage('Deployment') {
	    	steps {
				
//				sh 'sshpass -p "tomcat" scp target/gamutkart.war tomcat@172.17.04:/home/tomcat/distros/apache-tomcat-8.5.47///webapps'
//				sh 'sshpass -p "tomcat" ssh tomcat@172.17.0.4 "JAVA_HOME=/home/tomcat/distros/jdk1.8.0_221" "/home/tomcat/distros/apache-tomcat-8.5.47/bin/startup.sh"'

//sshagent(['tomcat-ssh']) {
//sh 'sudo scp -o StrictHostKeyChecking=no target/gamutkart.war tomcat@172.17.04:/home/tomcat/distros/apache-tomcat-8.5.47/webapps'
//}

sh 'sshpass -p tomcat scp target/gamutkart.war tomcat@172.17.0.4:/home/tomcat/distros/apache-tomcat-8.5.47/webapps'

sh 'sshpass -p tomcat ssh tomcat@172.17.0.4 "JAVA_HOME=/home/tomcat/distros/jdk1.8.0_221" "/home/tomcat/distros/apache-tomcat-8.5.47/bin/startup.sh"'


print "Deployment is done!"
	    	}
		}
    }
}
