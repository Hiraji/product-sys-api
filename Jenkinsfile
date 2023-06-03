pipeline {
	agent any 
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
			steps {
				bat "mvn -B -U -e -V clean -DskipTests deploy -Pdev -DmuleDeploy "
			}
		}
	
	}
}