node {
    stage('Build') {
        docker.image('3.9-bullseye').inside {
            sh 'python -m py_compile app.py'
            stash(name: 'compiled-results', includes: 'sources/*.py*')
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
        sh "sudo nohup python3 app.py > log.txt 2>&1 &"
        sh "sleep 60"
    }
}