pipeline {
    agent any
    stages {
        stage('plop') {
          steps {
            sh 'pwd'
            sh 'ls -al'
            sh 'touch toto'
          }
        }
        stage('BuildAndTest') {
            matrix {
                agent any
                axes {
                    axis {
                        name 'PLATFORM'
                        values 'linux', 'windows', 'mac'
                    }
                    axis {
                        name 'BROWSER'
                        values 'firefox', 'chrome', 'safari', 'edge'
                    }
                }
                stages {
                    stage('Build') {
                        steps {
                            echo "Do Build for ${PLATFORM} - ${BROWSER}"
                            sh 'pwd'
                            sh 'ls -al'
                        }
                    }
                    stage('Test') {
                        steps {
                            echo "Do Test for ${PLATFORM} - ${BROWSER}"
                            sh 'pwd'
                            sh 'ls -al'
                        }
                    }
                }
            }
        }
    }
  post {
    always {
      
      // delete workspace
      cleanWs()
    }
  }
}

