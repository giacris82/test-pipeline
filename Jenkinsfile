def notify = "john.doe@virtamed.net"
def testing = "all"
pipeline {
    agent any
	options {
                  timeout(time: 30, unit: 'MINUTES') 
             }
    stages {
	    
	    
        stage('Build_Installer') {
           environment {
			deploy = "true"
			revision = "4.2.1-rc1"
			}
	
		
            steps {
                echo '''Build_Installer stage variables'''
		echo "deploy: ${deploy} , notify: ${notify} , revision: ${revision}"
            }
        }
		stage('Build_Project_A') {
		environment {
			deploy = "false"
			revision = "1.2.3"
			}
            steps {
                    echo '''Build_Project_A stage variables '''
		    echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
            }
        }
		stage('Build_Project_B') {
			environment {
			deploy = "true"
			revision = "1.2.4"
			}
            steps {
                echo 'Build_Project_B stage variables'
		echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
            }
        }
		stage('Test_Project_A') {
			environment {
				module = "parsing"
				revision = "1.2.3"
				}
            steps {
                echo '''Test_Project_A stage variables'''
		echo "module: ${module} , revision: ${revision}"
            }
        }
		stage('Test_Project_B') {
		environment {
				module = "exporting"
				revision = "1.2.4"
				}
            steps {
                echo '''Test_Project_B stage varibles'''
		echo "module: ${module} , revision: ${revision}"
            }
        }
    }
}
