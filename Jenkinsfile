pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/anwar1622/TestingApi.git']]])
           }
        }
        stage('Test') {
            steps {
                sh 'mvn test -Dtest=TestRunnerProearn'
            }
        }
    }
    post {
        always {
            script {
                discordSend description: 'Jenkins Pipeline Build', footer: buildStatus, link: env.BUILD_URL, result: currentBuild.currentResult, unstable: false, title: JOB_NAME, webhookURL: 'https://discord.com/api/webhooks/1075366722246279238/DaMS73RWM7a7anWvpLf8TdY-iBUlvOZORfK2rxBC1Dh_rGVdfSdMW-1U4SCTm5ApCO_1'
                }
            }
        }
}
