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
            script {
                discordSend description: 'Jenkins Pipeline Build', footer: buildStatus, link: env.BUILD_URL, result: currentBuild.currentResult, unstable: false, title: JOB_NAME, webhookURL: 'https://discord.com/api/webhooks/1075390909027455106/wx0_2U9DD9NB74OXv6si6nq0ZkjKnTL-6hmoeE9h2dcvVxpNKF_ZR02MkRJILYghXHPl'
                }
            }
        }
}
