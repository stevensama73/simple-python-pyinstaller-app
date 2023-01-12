node {
    stage('Build') {
        docker.image('python:3.12.0a4-bullseye').inside {
            sh 'virtualenv venv && . venv/bin/activate && pip install flask && python -m py_compile app.py'
        }   
    }
    stage('Test') {
        docker.image('qnib/pytest').inside {
            sh 'py.test --verbose --junit-xml test-reports/results.xml test.py'
        }   
    }
    stage('Manual Approval') {
        input message: 'Lanjutkan ke tahap Deploy?' 
    }
    stage('Deploy') {
        sh "sudo nohup python app.py > log.txt 2>&1 &"
        sh "sleep 60"
    }
}