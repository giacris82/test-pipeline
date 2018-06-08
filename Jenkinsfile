pipeline {
    agent any
	options {
                  timeout(time: 30, unit: 'MINUTES') 
             }
    stages {
	    boolean deploy = true
	    def notify = "john.doe@virtamed.net" 
	    def revision = "4.2.1-rc1
	    
        stage('Build_Installer') {
            /*environment {
			deploy = "true"
			notify = "john.doe@virtamed.net"
			revision = "4.2.1-rc1"
			}*/
		
            steps {
                echo '''Build_Installer stage
			showing stage env'''
		    echo "deploy: ${deploy} , notify: ${notify} , revision: ${revision} "
            }
        }
		stage('Build_Project_A') {
		environment {
			deploy = "false"
			testing = "all"
			revision = "1.2.3"
			}
            steps {
                echo '''Build_Project_A stage
			showing stage env variables '''
		    echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
            }
        }
		stage('Build_Project_B') {
			environment {
			deploy = "true"
			testing = "all"
			revision = "1.2.4"
			}
            steps {
                echo 'Build_Project_B stage'
				echo 'showing stage env'
				echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
            }
        }
		stage('Test_Project_A') {
			environment {
				module = "parsing"
				revision = "1.2.3"
				}
            steps {
                echo 'Test_Project_A stage'
				echo 'showing stage env'
				echo "module: ${module} , revision: ${revision}"
            }
        }
		stage('Test_Project_B') {
		environment {
				module = "exporting"
				revision = "1.2.4"
				}
            steps {
                echo 'Test_Project_B stage'
				echo 'showing stage env'
				echo "module: ${module} , revision: ${revision}"
            }
        }
    }
}
