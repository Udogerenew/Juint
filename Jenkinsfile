pipeline{    
  agent any
    stages{
        stage('source code checkout'){
           steps{
            cleanWs()
//            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'afe961f5-1351-4b38-895d-293f0386bf31', url: 'https://github.com/Udogerenew/Juint.git']]])
             checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [[$class: 'SparseCheckoutPaths', sparseCheckoutPaths: [[path: '/ranga/ranga1']]]], userRemoteConfigs: [[credentialsId: 'afe961f5-1351-4b38-895d-293f0386bf31', url: 'https://github.com/Udogerenew/Juint.git']]])
	     sh 'ls -lrt' 
	   }
        }
        stage('test'){
           steps{
		   sh 'unzip test-output_2022-12-06T06_35_30.zip'
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
