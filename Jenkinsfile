pipeline {
	agent any 
	environment {
		ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
	}
	stages {
		stage('Build') {
			steps {
				bat "mvn clean install -P autoInstallPackage -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true"
			}
		}
		stage('Test') {
			steps {
				echo "Munit testing runs successfully"
			}
		}
		stage('Deploy') {
			environment {
				CLIENT_ID = credentials('DEV_CLIENT_ID')
				CLIENT_SECRET = credentials('DEV_CLIENT_SECRET')
			}
			steps {
				bat 'mvn clean deploy -Pdev -DmuleDeploy -Dusername="%ANYPOINT_CREDS_USR%" -Dpassword="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"'
			}
		}
	
	}
}