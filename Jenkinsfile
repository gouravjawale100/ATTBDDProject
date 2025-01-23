pipeline {
    agent any

    stages {
        stage('Fetching the code') {
            steps {
                git credentialsId: 'c630fc5b-20d7-41ae-b67c-6e792622e281', url: 'https://github.com/gouravjawale100/ATTBDDCucumberProject.git'
            }
        }

        stage('Execute the project on Chrome') {
            steps {
                bat "mvn -Dmaven.test.failure.ignore=true test -DcliBrowser=Chrome"
            }
             post { 
        always { 
            emailext attachLog: true, attachmentsPattern: 'target/amazontestreport/reports.html', body: '''<h1> Hi Team,</h1>
<p>Please find the details of execution below:<br>
$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:<br>
Check console output at $BUILD_URL to view the results.<br>

Thanks & Regards<br>

ATT 13 July''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS! - Customized email from jenkins', to: 'gouravatttest@gmail.com'
        }
    }

        }

        stage('Execute the project on firefox') {
            steps {
                bat "mvn -Dmaven.test.failure.ignore=true test -DcliBrowser=Firefox"
            }

             post { 
        always { 
            emailext attachLog: true, attachmentsPattern: 'target/amazontestreport/reports.html', body: '''<h1> Hi Team,</h1>
<p>Please find the details of execution below:<br>
$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:<br>
Check console output at $BUILD_URL to view the results.<br>

Thanks & Regards<br>

ATT 13 July''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS! - Customized email from jenkins', to: 'gouravatttest@gmail.com'
        }
    }
        }
        
    }

    
}
