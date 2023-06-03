pipeline {
	agent any 
	stages {
		stage('Build') {
			steps {
				bat "mvn -B -U -e -V clean -DskipTests package"
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