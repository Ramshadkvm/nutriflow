pipeline {
agent any

```
environment {
    NODE_HOME = 'C:\\Program Files\\nodejs'
    PATH = "C:\\Program Files\\nodejs;${env.PATH}"
}

stages {

    stage('Check Node') {
        steps {
            bat '''
                echo Checking Node.js...
                node --version
                npm --version
            '''
        }
    }

    stage('Install Backend Dependencies') {
        steps {
            bat '''
                echo Installing backend dependencies...
                if exist backend (
                    cd backend
                    if exist package.json (
                        npm install
                    ) else (
                        echo No backend package.json found.
                    )
                ) else (
                    echo Backend folder not found.
                )
            '''
        }
    }

    stage('Test Backend') {
        steps {
            bat '''
                echo Testing backend...
                if exist backend (
                    cd backend
                    if exist package.json (
                        npm test
                    ) else (
                        echo No backend package.json found.
                    )
                ) else (
                    echo Backend folder not found.
                )
            '''
        }
    }

    stage('Install Frontend Dependencies') {
        steps {
            bat '''
                echo Installing frontend dependencies...
                if exist frontend (
                    cd frontend
                    if exist package.json (
                        npm install
                    ) else (
                        echo No frontend package.json found.
                    )
                ) else (
                    echo Frontend folder not found.
                )
            '''
        }
    }

    stage('Test Frontend') {
        steps {
            bat '''
                echo Testing frontend...
                if exist frontend (
                    cd frontend
                    if exist package.json (
                        npm test
                    ) else (
                        echo No frontend package.json found.
                    )
                ) else (
                    echo Frontend folder not found.
                )
            '''
        }
    }

    stage('Build Frontend') {
        steps {
            bat '''
                echo Building frontend...
                if exist frontend (
                    cd frontend
                    if exist package.json (
                        npm run build
                    ) else (
                        echo No frontend package.json found.
                    )
                ) else (
                    echo Frontend folder not found.
                )
            '''
        }
    }
}

post {
    always {
        echo 'Jenkins pipeline finished.'
    }

    success {
        echo 'Build and tests completed successfully!'
    }

    failure {
        echo 'Build or tests failed.'
    }
}
```

}
