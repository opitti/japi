pipeline {
  agent { docker { image 'pythonssh:3.7.3-alpine3.10' } }
  stages {
    stage('build') {
      steps {
        sh """
        docker run -it --rm --name python3AWS -v "$PWD":/usr/src/myapp   -w /usr/src/myapp pythonssh:3.7.3-alpine3.10 sh
        python -m venv env
        source env/bin/activate
        pip install -r requirements.txt'
        """
      }
    }
    stage('test') {
      steps {
        sh """
        docker run -it --rm --name python3AWS -v "$PWD":/usr/src/myapp   -w /usr/src/myapp pythonssh:3.7.3-alpine3.10 sh
        source env/bin/activate
	python test.py
        """
      }   
    }
  }
}

