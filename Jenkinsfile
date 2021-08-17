def DOCKER_IMAGE_NAME="samsung-sds:5000/gitopspoc:v${CURRENT_BUILD}"
pipeline {
    parameters {
      string 'CURRENT_BUILD'
    }
    agent any
    stages
    {
        stage('Build: Code Repo')
        {
            steps
            {
                script
                {
                    sh "npm install"
                    sh "docker build -t samsung-sds:5000/gitopspoc:v${BUILD_NUMBER} ."
                    sh "docker push samsung-sds:5000/gitopspoc:v${BUILD_NUMBER}"
                    build job: 'update_gitops_repo_pipeline', parameters: [string(name: 'CURRENT_BUILD', value: '${BUILD_NUMBER}')]
                }
            }
        }
    }
}
