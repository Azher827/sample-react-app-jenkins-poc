def DOCKER_IMAGE_TAG="samsung-sds:5000/gitopspoc:v${BUILD_NUMBER}"
pipeline {
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
                    sh "docker build -t ${DOCKER_IMAGE_TAG} ."
                    sh "docker push ${DOCKER_IMAGE_TAG}"
                    build job: 'update_gitops_repo_pipeline', parameters: [string(name: 'DOCKER_IMAGE_NAME', value: "${DOCKER_IMAGE_TAG}")]
                }
            }
        }
    }
}
