node('docker'){
    def customImage //variable to define the built image
    
    stage('Checkout SCM'){
        checkout scm
        }
        
    stage('Docker build'){
        customImage = docker.build("myimage:${env.BUILD_ID}") //build the image in the docker file using the tag as "myImage:build_number"
        }
        
    stage('Docker push'){
            docker.withRegistry('https://docker-registry-pl-test-31.pl.s2-eu.capgemini.com/', '02b7f7c3-2109-4970-bd30-a664bcb40463') { //Push the image to private registry 
            customImage.push()
            }
        }
}
