pipeline{
    agent any
    environment{
    email = "onyi.okorie1995@gmail.com"
    integration_testtool = "TestComplete"
    unit_testtool = "JUnit"
    buildtool = "Maven"
    codeanalysistool ="CheckStyle"
    securitytool = "Acunetix"
    stagingserver = "Azure Virtual Machine"
    productionserver = "AWS EC2 Instance"
 }
    stages{
        stage("Build"){
            steps{
                echo "Building the code using $buildtool to compile and package code."
            }
        }
        stage("Unit and Integration Tests"){
            steps{
                echo "Run unit tests using $unit_testtool to ensure the code functions as expected and run integration tests using $integration_testtool to ensure the different components of the application work together as expected."
            }
            post{
                success{
                    emailext attachLog: true, to: "$email",
                    subject: "Unit Tests Status Email",
                    body: "Test was successful!"
                    
                }
                failure{
                    emailext attachLog: true, to: "$email",
                    subject: "Tests Status Email",
                    body: "Test Failed!"
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "Integrate $codeanalysistool to analyse the code and ensure it meets industry standards"
            }
        }
        stage("Security Scan"){
            steps{
                echo "perform a security scan on the code using a $securitytool to identify any vulnerabilities."
            }
            post{
                success{
                    emailext attachLog: true, to: "$email",
                    subject: "Security Scan Status Email",
                    body: "Security scan was successful!"
                }
                failure{
                    emailext attachLog: true, to: "$email",
                    subject: "Security Scan Status Email",
                    body: "Security scan Failed!"
                }
            }
        }
        stage("Deploy to Staging"){
            steps{
                echo "Deploy the application to a $stagingserver"
            }
        }
        stage("Integration Tests on Staging"){
            steps{
                echo "Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment."
            }
            post{
                success{
                    emailext attachLog: true, to: "$email",
                    subject: "Integration Tests Status Email",
                    body: "Integration Test was successful. Yay!"
                }
                failure{
                    emailext attachLog: true, to: "$email",
                    subject: "Integration Tests Status Email",
                    body: "Integration Test Failed! Oh No!"
                }
            }
        }
        stage("Deploy to Production"){
            steps{
                echo "Deploy the application to a $productionserver"
            }
        }
    }
}