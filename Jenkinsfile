node {
    docker.image('python').inside {
        stage('Build') {
            sh 'python -m py_compile /sources/add2vals.py /sources/calc.py'
        }
    }
    docker.image('qnib/pytest').inside {
        stage('Test') {
            sh 'py.test --verbose --junit-xml test-reports/results.xml /sources/test_calc.py'
        }
    }
}