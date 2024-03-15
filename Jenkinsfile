dev gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.0', '2.0', '3.0'], description: 'Which version would you like to build?')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Should we execute the tests?')
        string(name: 'GREETING', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
    
    stages {
        stage('init') {
            steps {
                gv = load "script.groovy"
            }
        }
        
        stage('build') {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }

        stage('test') {
            steps {
                script {
                    if (params.executeTests) {
                        gv.testApp()
                    }
                }
            }
        }
        
        stage('deploy') {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }
}