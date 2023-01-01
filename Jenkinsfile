node {
    docker.image('python:2-alpine').inside {
        stage('Build') {
            sh 'python -m py_compile add2vals.py calc.py'
        }
    }
    docker.image('qnib/pytest').inside {
        stage('Test') {
            sh 'py.test --verbose --junit-xml test-reports/results.xml test_calc.py'
        }
    }
}