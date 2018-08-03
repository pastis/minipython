pipeline {
  agent any
  stages {
    stage('Setup Phase ') {
      steps {
        echo 'Merge Request Hook Firedd'
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
        stage('Database Merge Test ') {
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
  }
}


