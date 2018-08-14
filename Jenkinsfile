/* import shared library  */
@Library('jenkins-shared-library')

pipeline {
  agent any
  stages {
    stage('Setup Phase ') {
      steps {
        echo 'Merge Request Hook Actuated'
      }
    }
    stage('Static Analysis') {
      parallel {
        stage('CHANGELOG') {
          steps {
            echo 'Valadating Changelog'
          }
        }
        stage('JavaScript') {
          steps {
            echo 'Envoking JSLint'
          }
        }
        stage('Python Pylint') {
          steps {
            echo 'Running PyLint'
          }
        }
        stage('Database ') {
          steps {
            echo 'Database Lint'
          }
        }
      }
    }
    stage('Unit Testing') {
      parallel {
        stage('CHANGELOG Unit') {
          steps {
            echo 'ChangeLog Unit Test'
          }
        }
        stage('JSUnit') {
          steps {
            echo 'Run JSUnit'
          }
        }
        stage('Pytest -m Unit') {
          steps {
            echo 'Run Unit test via pytest'
          }
        }
        stage('Database Unit ') {
          steps {
            echo 'Run Unit Tests for DB '
          }
        }
      }
    }
    stage('Merge Request') {
      parallel {
        stage('Candate Database Merge ') {
          steps {
            echo 'Merge DB'
          }
        }
        stage('Candidate Source Merge ') {
          steps {
            echo 'Merge Build'
          }
        }
      }
    }
    stage('Test Merge') {
      parallel {
        stage('Test Database Merge ') {
          steps {
            echo 'Test DB'
          }
        }
        stage('Test Source Merge ') {
          steps {
            echo 'Test Build'
          }
        }
      }
    }
     stage('Make RPM') {
       steps {
            echo 'Create RPM'
          }
        }
     stage('Deploy RPM to Dev  ') {
          steps {
            approve()
            echo 'Run-Generic'
          }
        }
     stage('Acceptance Test Dev  ') {
          steps {
            echo 'UI Accptance'
          }
        }  
      }
}
 
def approve() {

	timeout(time:1, unit:'DAYS') {
		input('Do you want to deploy to live?')
	}

}
