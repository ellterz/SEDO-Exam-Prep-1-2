pipeline{
    agent any

    stages{
        stage("Restore the dependencies"){
            when{ branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP"}
            steps{
                sh 'dotnet restore'
            }
        }
    }
    stages{
        stage("Bild the application"){
            when{ branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP"}
            steps{
                sh 'dotnet build --no-restore'
            }
        }
    }
    stages{
        stage("Run the test"){
            when{ branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP"}
            steps{
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}