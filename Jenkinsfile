pipeline {
    agent any
    stages {
        stage('Example Build') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Example Deploy') {
            when {
               // branch 'origin/production'  does not work. it is replaced b the folowing expression 
               // See https://issues.jenkins-ci.org/browse/JENKINS-43104?page=com.atlassian.jira.plugin.system.issuetabpanels%3Aall-tabpanel
                expression {
                  return env.GIT_BRANCH == "origin/master"
                }
                anyOf {
                    environment name: 'DEPLOY_TO', value: 'production'
                    environment name: 'DEPLOY_TO', value: 'staging'
                }
            }
            steps {
                echo 'Deploying'
            }
        }
    }
}