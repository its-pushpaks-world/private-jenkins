pipeline {
   agent any
   tools {
        terraform 'terraform'
        } 
	
	
   stages {
       
    stage('Terraform init') {
      steps {
              //terraform init >> test.log 
	      sh '''
               echo "Terraform Init"
               pwd >> test.log
               '''
           }   
    }
    
    stage('Terraform plan') {
    steps {
             //sh 'terraform plan '
	    echo "Terraform Plan"
           }   
    }
        
    stage('Terraform apply') {
    steps {
             //sh 'terraform apply --auto-approve'
             echo "Terraform Apply"
	     sh 'cat test.log'
           }   
    }   
    
    stage('Run other pipeline') {
    steps {
              build job: 'Test_Parameter', parameters: [string(name: 'Option', value: 'Create')]
            }
        }
        
    }
    
post {
	success { 
	  script{
		    
		emailext to: "itspushpaksworld496@gmail.com",
		subject: "Terraform Build successfully",
      	        body: "Hello User,\n\nJob ${env.JOB_NAME} executed successfully. \nRefer this URL to know more: ${env.BUILD_URL}"
       	        attachlog: true
        	attachmentsPattern: "test.log"
				
			}
		}
	}    
    
  }
