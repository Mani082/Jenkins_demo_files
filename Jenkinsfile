node
{
stage('checkout')
{
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Mani082/Jenkins_demo_files.git']]])
}
stage('Build')
{
    powershell 'javac HelloAll.java'
    powershell 'java HelloAll'
    powershell 'echo "The build number is ${env:BUILD_NUMBER}"'
    
}
stage('Test')
{
    echo "Testing.."
}
stage('Deploy')
{
    powershell 'jfrog rt c my_server --url=http://localhost:8081/artifactory --user=admin --password=Mani@123'
    powershell 'jfrog rt u HelloAll.class version_demo_repo/build_version_${env:BUILD_NUMBER}/'
}
}
