pipeline
{
    agent any
    stages
    {
        stage("Clone the Application code")
        {
            steps
            {
                git branch: 'main', url: 'https://github.com/sravya-07/my-node-js-app.git'
            }
        }

        stage("Build the Dockerfile to create the image")
        {
            steps
            {
                sh'''
                    cd ${WORKSPACE}
                    docker build . -t mynodejsapp:v1
                '''

            }
        }

        stage("Tag the Docker iamge for the repository")
        {
            steps
            {
                sh '''
                    docker tag mynodejsapp:v1 sravya1/mynodejsapp:latest
                '''
            }
        }

        stage("Login & Push the image to the repository")
        {
            steps
            {
                sh '''
                    docker login sravya1/mynodejsapp
                    docker push sravya1/mynodejsapp:latest
                '''
            }

        }
    }
}
