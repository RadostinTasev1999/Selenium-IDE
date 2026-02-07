/*
Steps:

1. Checkout the code
2. Set up .NET Core
3. Uninstall current chrome
4. Install specific version of Chrome
5. Download and install ChromeDriver
6. Restore dependencies
7. Build
8. Run tests
 */

 pipeline {
    agent any

    

    stages {
        
        stage('Restore dependencies'){
            steps {
                // Restore dependencies using the solution file
                bat 'dotnet restore SeleniumIde.sln'
            }
            post {
                failure {
                    echo "Step failed"
                }
            }
        }

        stage('Build solution') {
            steps {
                // Build the project using the solution file
                bat 'dotnet build SeleniumIde.sln'
            }
        }

        stage('Run tests') {
            steps {
                // Run tests using the solution file
                bat 'dotnet test SeleniumIde.sln -- no-build --verbosity normal'
            }    
        }
        
    }  
    
    post {
        always {
            echo "Workflow completed successfully"
        }
    }
        
}