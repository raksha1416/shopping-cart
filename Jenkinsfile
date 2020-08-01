
pipeline {
  agent any
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('SCM Checkout') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/pranshulgupta/shopping-cart.git'
      }
    }
  }
}
