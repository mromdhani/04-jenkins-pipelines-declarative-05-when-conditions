pipeline {

    agent any
    stages {
        stage('Example Build') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Example Deploy MAIN') {
            when {
               // branch 'origin/production'  does not work. it is replaced b the folowing expression 
               // See https://issues.jenkins-ci.org/browse/JENKINS-43104?page=com.atlassian.jira.plugin.system.issuetabpanels%3Aall-tabpanel
                expression {
                  return env.GIT_BRANCH == "origin/main"
                }
            }
            steps {
                echo 'Deploying to MAIN '
            }
        }
        stage('Example Deploy DEV') {
            when {
               // branch 'origin/production'  does not work. it is replaced b the folowing expression 
               // See https://issues.jenkins-ci.org/browse/JENKINS-43104?page=com.atlassian.jira.plugin.system.issuetabpanels%3Aall-tabpanel
                expression {
                  return env.GIT_BRANCH == "origin/dev"
                }
            }
            steps {
                echo 'Deploying to DEV '
            }
        }
    }
}