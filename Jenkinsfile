@Library('piper-lib-os') _

//abapEnvironmentPipeline script: this

pipeline {
  agent any
  
  
  stages {
    stage ('Run Unit Tests') {
      steps {
        abapCi abapPackagename: 'S_NWDEMO', runUnitTests: true
      }
    }
  }
}
