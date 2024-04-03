pipeline {
    agent any
    stages {
        stage('Build dock') {
            when {
                changeset "**/dock/*"
                beforeAgent true
            }
            steps {
                dir('dock') {
                 echo 'test'
                }
            }
        }
        stage('Build jest') {
            when {
                changeset "**/jest/*.*"
                beforeAgent true
            }
            steps {
               dir ('jest') {
                 echo 'test jest'
               }
            }
        }
    }
}
