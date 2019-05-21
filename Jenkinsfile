pipeline {
    agent any
    parameters {
      string(name: 'PLANET', defaultValue: 'Earth', description: 'Which planet are we on?')
      string(name: 'GREETING', defaultValue: 'Hello', description: 'How shall we greet?')
    }
    triggers {
        cron('* * * * *')
        parameterizedCron('''
# leave spaces where you want them around the parameters. They'll be trimmed.
# we let the build run with the default name
0 12 * * 2 %GREETING=Hola;PLANET=Pluto
5 12 * * 2 %PLANET=Mars
        ''')
    }
    stages {
        stage('Example') {
            steps {
                echo "${GREETING} ${PLANET}"
                script { currentBuild.description = "${GREETING} ${PLANET}" }
            }
        }
    }
}
