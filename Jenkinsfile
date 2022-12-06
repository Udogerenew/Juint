pipeline{    
  agent any
    stages{
        stage('source code checkout'){
           steps{
            cleanWs()
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'afe961f5-1351-4b38-895d-293f0386bf31', url: 'https://github.com/Udogerenew/Juint.git']]])
           }
        }
        stage('test'){
           steps{
		  'sh 'printenv''
//               junit allowEmptyResults: true, testResults: "${WORKSPACE}/log.xml"
                	    publishHTML (target: [
	 	            allowMissing: false,
	 	            alwaysLinkToLastBuild: false,
	 	            keepAll: true,
	 	            reportDir: "${workspace}",
	 	            reportFiles: "*.html",
	 	            reportName: "Test_report"])
               junit skipPublishingChecks: true, testResults: '*.xml'
            }
        }
    }
}
