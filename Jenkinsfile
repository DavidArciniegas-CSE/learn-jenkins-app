pipeline{
    agent any
    stages{
        stage('Build'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la 
                '''
            }    
        }
        stage('Test'){
            steps{
                sh '''
                    echo "test stage"
                    cd build/
                    test -f index.html
                    cd ..
                    CI=true npm test
                '''
            }    
        }
    }
}