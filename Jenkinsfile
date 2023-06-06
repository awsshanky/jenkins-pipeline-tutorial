// Declarative pipelines must be enclosed with a "pipeline" directive.
pipeline {
    // This line is required for declarative pipelines. Just keep it here.
	
    agent {
        node {

        label 'aws_slave_ec2'

        }

    }

    // This section contains environment variables which are available for use in the
    // pipeline's stages.
  /*  environment {
	    region = "eu-north-1"
        docker_repo_uri = "public.ecr.aws/t4o8m4g4/docker"
		task_def_arn = ""
        cluster = ""
        exec_role_arn = ""
    } */
    
    // Here you can define one or more stages for your pipeline.
    // Each stage can execute one or more steps.
    stages {
        // This is a build stage.
        stage('Build') {
    steps {
   
        script {
            docker.withRegistry(
		    'https://209264512117.dkr.ecr.eu-north-1.amazonaws.com',
		    'ecr:eu-north-1:aws_slave_key') {
		    def myImage = docker.build('public.ecr.aws/t4o8m4g4/docker')
		    myImage.push('latest')
       
            }
        }
    }
}
