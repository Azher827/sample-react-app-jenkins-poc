def DOCKER_IMAGE_TAG="samsung-sds:5000/gitopspoc:v${BUILD_NUMBER}"
pipeline {
    agent any
    triggers {
       pollSCM '* * * * *'
    }
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
                    build job: 'deployment_react_app_pipeline', parameters: [string(name: 'DOCKER_IMAGE_NAME', value: "${DOCKER_IMAGE_TAG}")]
                }
            }
        }
    }
}
