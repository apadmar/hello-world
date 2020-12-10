node('docker'){
    def customImage //variable to define the built image
    
    stage('Checkout SCM'){
        checkout scm
        }
        
    stage('Docker build'){
        customImage = docker.build("myimage:${env.BUILD_ID}") //build the image in the docker file using the tag as "myImage:build_number"
        }
        
    stage('Docker push'){
            docker.withRegistry('https://docker-registry-pldemo01.pl.s2-eu.capgemini.com/', '9fe24276-4593-4599-8778-f31e4de846fb') { //Push the image to private registry 
            customImage.push()
            }
        }
}
