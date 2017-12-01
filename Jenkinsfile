pipeline {
    agent any
    stages {
       
        stage('build') {
            steps {
                echo 'realizando la build'
                bat './gradlew build'
            }
        }
          stage('metricas') {
            steps {
                echo 'subiendo las metricas'
                bat 'cd D:\Jorge\Downloads\Programas\sonarqube-6.5\bin\windows-x86-64'
                bat './StartSonar.bat'
                echo 'El servidor SonarQube debe estar arriba'
                bat 'cmd D:\Jorge\Dropbox\Udea\2017-1\Proyecto Integrador I\workspace\Calculadora'
                bat './gradlew sonarqube'
            }
        }
        stage('repositorioActivos'){
            steps {
                echo 'subiendo al repositorio de activos las librerias'
                bat './gradlew uploadArchives'
            }
        }
    }
    post{
        success {
            echo 'El pipeline se ejecuto exitosamente'
        }
        failure {
            echo 'Ha ocurrido un error en la ejecucion del pipeline'
        }
        changed {
            echo 'El estado ha cambiado, revisar'
        }
    }
}
