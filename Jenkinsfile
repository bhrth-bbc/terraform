pipeline
{
    agent any
    stages
	{
	stage('test')
	    {
		steps
		    {
    			withCredentials([string(credentialsId: 'accesskey', variable: 'accesskey')]) { //set SECRET with the credential content
        		//echo "My secret text is '${access}'"
				withCredentials([string(credentialsId: 'secretkey', variable: 'secretkey')]) { //set SECRET with the credential content
        			//echo "My secret text is '${secr}'"
					withCredentials([file(credentialsId: 'public', variable: 'public')]) {
						withCredentials([file(credentialsId: 'private', variable: 'private')]) {
				sh 'terraform init -no-color'
				sh 'terraform apply -auto-approve -no-color -var "accesskey=$accesskey" -var "secretkey=$secretkey" -var "public=$public" -var "private=$private"'
			}
    		}
				}
			}
		}
	    }
	}
}
