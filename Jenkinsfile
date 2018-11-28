pipeline {
  agent any
	
  triggers {
    pollSCM('* * * * *')
  }
	
  stages {
    stage("Compile") {
      steps {
        sh "./gradlew compileJava"
      }
    }
	  
    stage("Unit test") {
      steps {
        sh "./gradlew test"
      }
    }
	

    stage("Build") {
      steps {
        sh "./gradlew build"
      }
    }

    stage("Docker build") {
      steps {
        sh "docker build -t ameena06/calculator:tag1 ."
      }
    }

    stage("Docker login") {
      steps {
        withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'ameena06',
                          usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
          sh "docker login --username ameena06 --password Firnny29"
        }
      }
    }

    stage("Docker push") {
      steps {
        sh "docker push ameena06/calculator:tag1"
      }
    }

    stage("Deploy to staging") {
      steps {
        sh "echo ansible script"
        sleep 60
      }
    }

    stage("Acceptance test") {
      steps {
	sh "echo acceptance test script"
      }
    }
	  
    // Performance test stages

    stage("Release") {
      steps {
        sh "echo command"
        sleep 60
      }
    }

  }
}
