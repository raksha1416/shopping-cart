
pipeline {
  agent any
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('git') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/pranshulgupta/shopping-cart.git'
      }
    }
  }
}
