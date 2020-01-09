pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'marco.contreras@softtek.com',
                                  passwordVariable: 'Pokemon3608$']]) {

                    sh '/usr/local/bin/cf login -a http://api.run.pivotal.io -u $marco.contreras@softtek.com -p $Pokemon3608$'
                    sh '/usr/local/bin/cf push'
                }
            }

        }

    }

}