pipeline{
	agent any
	stages {
		stage('git checkout'){
			steps{
				checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jacksontechtraining/piplinepython12121']])
			}
		}
		stage('dependency'){
			steps{
				echo 'installing dependency'
				bat 'python -m pip install -r requirements.txt'
			}
		}
		stage('check migration'){
			steps{
				echo 'checking for DB changes'
				bat 'python manage.py migrate'
			}
		}
		stage('migrate'){
			steps{
				echo 'making DB changes'
				bat 'python manage.py makemigrations'
			}
		}
		stage('testing'){
			steps{
				echo 'Running testcases'
				bat 'python manage.py test'
			}
		}
	}
}