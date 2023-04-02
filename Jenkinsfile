pipeline {

  agent any
  stages {
    stage('mvn clean install') {
      steps {
        // One or more steps need to be included within the steps block.
        withMaven(globalMavenSettingsConfig: 'null', jdk: 'null', maven: 'M3', mavenSettingsConfig: 'null') {
          // some block

          sh 'mvn clean install'

        }

      }
    }

    stage('mvn test') {
      steps {

        withMaven(globalMavenSettingsConfig: 'null', jdk: 'null', maven: 'M3', mavenSettingsConfig: 'null') {

          sh 'curl -O https://downloads.lambdatest.com/tunnel/v3/mac/64bit/LT_Mac.zip'
          sh 'unzip LT_MAC.zip'

          sh 'export LT_USERNAME=${env.LT_USERNAME}'
          sh 'export LT_ACCESS_KEY=${env.LT_ACCESS_KEY}'

          sh "./LT  --user ${LT_USERNAME} --key ${LT_ACCESS_KEY} &"

          sh 'mvn test -D suite=parallel.xml'

          // some block

        }

        // One or more steps need to be included within the steps block.
      }
    }

  }
}
