pipeline {
    agent any

    triggers {
        cron('H/5 * * * *')   // run every 5 minutes
    }

    stages {
        stage('Delete Temp Files from /var/tmp') {
            steps {
                sh '''
                  echo "Deleting temp files older than 5 minutes from /var/tmp..."
                  find /var/tmp \
                    -path "/var/tmp/systemd-private-*" -prune -o \
                    -type f -mmin +5 -exec rm -f {} \\;
                '''
            }
        }
    }
}
