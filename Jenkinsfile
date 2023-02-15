pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/anwar1622/TestingApi.git']]])
           }
        }
//         stage('Test') {
//             steps {
//                 sh 'mvn test -Dtest=ExamplesTest'
//             }
//         }
    }
    post {
        always {
            discordSend description: 'Jenkins Pipeline Build', footer: buildStatus, link: env.BUILD_URL, result: currentBuild.currentResult, unstable: false, title: JOB_NAME, webhookURL: 'https://discord.com/api/webhooks/1075395141554147379/-CmvZjEhcutOS-gIxorQ5TXmEE_5DtV1g2xII3HrnkjNUBV2jN2YdbCb7KTMcRm8zTyG'
            }
        }
}
