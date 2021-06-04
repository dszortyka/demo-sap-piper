//@Library('piper-lib-os') _
@Library('piper-lib-os@v1.145.0') _

//library('piper-lib-os')
//gctsCloneRepository script: this

pipeline {
  agent any
  stages {
    stage ('Run Unit Tests') {
      steps {
        abapCi abapPackagename: 'S_NWDEMO', runUnitTests: true
      }
    } //stage 
    stage ('Run ATC Checks') {
      steps {
        abapCi abapPackagename: 'S_NWDEMO', runAtcChecks: true
      }
    }
    stage ('gctsCloneRepository') {
      steps {
        gctsCloneRepository(
          script: this,
          host: 'https://192.168.15.40:50001',
          client: '001',
          abapCredentialsId: 'ABAPUserPasswordCredentialsId_A4H',
          repository: 'devzdemo'
        )
      }
    }
  }
}
