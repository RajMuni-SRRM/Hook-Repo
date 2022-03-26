pipeline {
    agent any
    stages{
        stage ('git checkout'){
            steps{
                git credentialsId: 'GitAuthone', url: 'https://github.com/RajMuni-SRRM/Hook-Repo.git'
            }
        }
        stage ('Build Artifact'){
            steps{
                sh 'mvn install'
            }
        }
        stage ('Checkstyle anyalysis'){
            steps{
                sh 'mvn checkstyle:checkstyle pmd:pmd findbugs:findbugs'
            }
        }
        stage ('Analysis'){
            steps{
                recordIssues(tools: [checkStyle(), pmdParser(), findBugs(useRankAsPriority: true)])
            }
        }
        
    }

}
