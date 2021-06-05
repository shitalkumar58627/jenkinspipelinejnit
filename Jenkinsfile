pipeline {

    agent any
    stages {

        stage('Cloning Git'){
            steps{
               echo " added suscesfully"
               git 'https://github.com/shitalkumar58627/jenkinspipelinejnit.git'
            }
        }

        stage('Build'){
            steps{
                sh 'mkdir lib1'
                sh 'cd lib1/ ; wget https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.7.0/junit-platform-console-standalone-1.7.0-all.jar'
                sh 'cd src ; javac -cp "../lib/junit-platform-console-standalone-1.7.0-all.jar" CarTest.java Car.java App.java'
            }
        }

        stage('Test'){
            steps{
                sh 'cd src/ ; java -jar ../lib/junit-platform-console-standalone-1.7.0-all.jar -cp "." --select-class CarTest --reports-dir="reports"'
                junit 'src/reports/*-jupiter.xml'
            }
        }

        stage('Deploy'){
            steps{
                sh 'cd src/ ; java App' 
            }
        }
    }

}
