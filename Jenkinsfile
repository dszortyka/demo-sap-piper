//@Library('piper-lib-os') _
@Library('piper-lib-os@v1.145.0') _

//library('piper-lib-os')
//gctsCloneRepository script: this

pipeline {
  agent any
  stages {
   // stage ('Run Unit Tests') {
   //   steps {
   //     abapCi abapPackagename: 'S_NWDEMO', runUnitTests: true
   //   }
   // } //stage 
   // stage ('Run ATC Checks') {
   //   steps {
   //     abapCi abapPackagename: 'S_NWDEMO', runAtcChecks: true
   //   }
   // }
    
    
    stage ('gctsExecuteABAPUnitTests') {
      steps {
        gctsExecuteABAPUnitTests(
          script: this,
          host: 'http://vhcala4hci:50000',
          client: '001',
          abapCredentialsId: 'ABAPUserPasswordCredentialsId_A4H',
          repository: 'zdemo'
        )
      }
    }
    stage ('gctsCloneRepository') {
      steps {
        gctsCloneRepository(
          script: this,
          host: 'http://vhcala4hci:50000',
          client: '001',
          abapCredentialsId: 'ABAPUserPasswordCredentialsId_A4H',
          repository: 'zdemo'
        )
      }
    }
    stage ('gctsDeploy') {
      steps {
        gctsDeploy(
          script: this,
          host: 'http://vhcala4hci:50000',
          client: '001',
          abapCredentialsId: 'ABAPUserPasswordCredentialsId_A4H',
          repository: 'zdemo',
          remoteRepositoryURL: "https://github.com/dszortyka/demo-sap-piper.git",
          role: 'TARGET',
          vSID: 'Z4H',
          //branch: 'main',
          commit: 'b536287212dcfb8642cd5ecccda5afe7ca0d3dce',
          //scope: 'scope',
          //rollback: false
          //configuration:
          //    dummyconfig: "dummyval"
        )
      }
    }
  } //stages
} //pipeline
