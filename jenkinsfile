pipeline{
	agent any
	
	stages{
		stage ("Test){
			steps {	
			script {
          				env.USERNAME = input message: 'Please enter the username',
                            	parameters: [string(defaultValue: '',
                              description: '',
                              name: 'Username')]

				}
					echo ${env.USERNAME}
				}
			}
		}
}
