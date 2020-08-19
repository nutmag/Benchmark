pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    
      stage ('Semgrep') {
      steps {
        sh 'rm semgrep || true'
        sh 'docker run --rm -v "$/root/Benchmark:/src" returntocorp/semgrep --config=https://semgrep.dev/p/nutmag.dvja-test
        sh 'cat semgrep'
      }
    }
    
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
    
   }
}
