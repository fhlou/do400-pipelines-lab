pipeline {
    agent any
    parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }
    stages {
        stage ('Test'){
        parallel {
            stage ('Unit_tests') {
                steps {
                    sh './mvnw test -D testGroups=unit'
                }
                
            }      
            stage ('Integration_tests'){
                when {
                    expression { return params.RUN_INTEGRATION_TESTS }
                }
                steps {
                    sh './mvnw test -D testGroups=integration'
                }
               
            }
        }
        }
    }
}