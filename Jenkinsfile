node {
    def app
    
    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'joaquinniram', passwordVariable: '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', usernameVariable: 'joaquinniram')]) {
                        sh "git config user.email joaquin.niram@gmail.com"
                        sh "git config user.name joaquinniram"
                        sh "cat vote-ui-deployment.yaml"
                        sh "sed -i 's+joaquinniram/vote.*+joaquinniram/vote:${DOCKERTAG}+g' vote-ui-deployment.yaml"
                        sh "cat vote-ui-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job deployment: ${env.BUILD_NUMBER}'"
                        sh "git push https://joaquinniram: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@github.com/joaquinniram/vote-deploy.git HEAD:master"
      }
    }
  }
}
}
