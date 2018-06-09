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
			     echo "Starting ${STAGE_NAME} stage with variables:"
			     echo "deploy: ${deploy} , notify: ${notify} , revision: ${revision}"
		     }
		     post {
		    always { 
			    echo "Finished ${STAGE_NAME}"
		    }
		    failure { 
			    echo "${STAGE_NAME} Failed!!!"
			    mail to: ${notify}, subject: "The Stage ${STAGE_NAME} failed!!!"
		    }
		    success { 
			    echo "${STAGE_NAME} Successful!!"
		    }
	     }
	    
	    }
	    stage('Build_Project_A') {
		    environment {
			    deploy = "false"
			    revision = "1.2.3"
		    }
		    steps {
			    echo "Starting ${STAGE_NAME} stage with variables"
			    echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
		    }
		    post {
			    always {
				    echo "Finished ${STAGE_NAME}"
		    }
		    failure { 
			    echo "${STAGE_NAME} Failed!!!"
		    }
		    success { 
			    echo "${STAGE_NAME} Successful!!"
		    }
	    }
	    }

	    stage('Build_Project_B') {
		    environment {
			    deploy = "true"
			    revision = "1.2.4"
		    }
            steps {
		    echo "Starting ${STAGE_NAME} stage with variables"
		    echo "deploy: ${deploy} , testing: ${testing} , revision: ${revision}"
            }
		    post {
		    always { 
			    echo "Finished ${STAGE_NAME}"
		    }
		    failure { 
			    echo "${STAGE_NAME} Failed!!!"
		    }
		    success { 
			    echo "${STAGE_NAME} Successful!!"
		    }
	    }
        }
	
	    stage('Test_Project_A') {
			environment {
				module = "parsing"
				revision = "1.2.3"
				}
            steps {
		    echo "Starting ${STAGE_NAME} stage with variables"
		    echo "module: ${module} , revision: ${revision}"
            }
		    post {
		    always { 
			    echo "Finished ${STAGE_NAME}"
		    }
		    failure { 
			    echo "${STAGE_NAME} Failed!!!"
		    }
		    success { 
			    echo "${STAGE_NAME} Successful!!"
		    }
	    }
        }
	
	    stage('Test_Project_B') {
		environment {
			module = "exporting"
			revision = "1.2.4"
		}
		    steps {
			    echo "Staring ${STAGE_NAME} stage with varibles:"
			    echo "module: ${module} , revision: ${revision}"
            }
		    post {
		    always { 
			    echo "Finished ${STAGE_NAME}"
		    }
		    failure { 
			    echo "${STAGE_NAME} Failed!!!"
		    }
		    success { 
			    echo "${STAGE_NAME} Successful!!"
		    }
	    }
        }
	
    }
}
