#!groovy
pipeline {
    agent none

            stages {
                currentBuild.result = "SUCCESS"

                try {
                        stage('Checkout') {
                            checkout scm
                        }

                        stage('Test') {

                            env.NODE_ENV = "test"

                            println("Environment will be : ${env.NODE_ENV}")

                        }

                        stage('Build Docker') {
                            def msg = powershell(returnStdout: true, script: 'Write-Output "Docker build!"')
                            println msg
                        }

                        stage('Deploy') {

                            println('Push to Docker registry')
                        }

                        stage('Cleanup') {

                            println('prune and cleanup')

//            mail body: 'project build successful',
//                    from: 'xxxx@yyyyy.com',
//                    replyTo: 'xxxx@yyyy.com',
//                    subject: 'project build successful',
//                    to: 'yyyyy@yyyy.com'
                        }
                }
                catch (err) {

                    currentBuild.result = "FAILURE"

//        mail body: "project build error is here: ${env.BUILD_URL}" ,
//                from: 'xxxx@yyyy.com',
//                replyTo: 'yyyy@yyyy.com',
//                subject: 'project build failed',
//                to: 'zzzz@yyyyy.com'

                    throw err
                }
        }

}