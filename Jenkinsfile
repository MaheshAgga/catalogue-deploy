pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    //  environment { 
    //     packageVersion = ''
    //     nexusURL = '172.31.36.234:8081'
    // }
    options {
       timeout(time: 1, unit: 'HOURS')
       disableConcurrentBuilds()
        ansiColor('xterm')
   }

   parameters {
         string(name: 'version', defaultValue: '1.2.0', description: 'What is the artifact version?')
         string(name: 'environment', defaultValue: 'dev', description: 'What is the environment?')

   }
    stages {
        stage('print the version') {
            steps {
               sh """
                    echo "version: ${params.version}
                    echo "environment: ${params.environment}
               """
            }
        }
        stage('Init') {
            steps {
               sh """
                    cd terraform
                    terraform init --backend-config=${params.environment}/backend.tf
               """
            }
        }
        //  stage('plan') {
        //     steps {
        //        sh """
        //             cd terraform
        //             terraform plan -var-file=${params.environment}/${params.environment}.tfvars
        //        """
        //     }
        // }
    }      
    //post build
    post {
        always {
            echo 'I will always says HareKrishna HareRama......'
            deleteDir()
        }
        failure{
            echo 'failure'
        }
        success{
            echo 'krishna success'
        }
    }
}
