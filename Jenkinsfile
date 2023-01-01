node {
    docker.image('python').inside {
        stage('Build') {
            sh 'python -m py_compile simple-python-pyinstaller-app/sources/add2vals.py simple-python-pyinstaller-app/sources/calc.py'
        }
    }
    docker.image('qnib/pytest').inside {
        stage('Test') {
            sh 'py.test --verbose --junit-xml test-reports/results.xml simple-python-pyinstaller-app/sources/test_calc.py'
        }
    }
}