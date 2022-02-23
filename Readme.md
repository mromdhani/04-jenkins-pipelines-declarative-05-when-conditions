# Jenkins Decalarative Pipeline Syntax / When
---
The when directive allows the Pipeline to determine whether the stage should be executed depending on the given condition. The when directive must contain at least one condition. If the when directive contains more than one condition, all the child conditions must return true for the stage to execute. This is the same as if the child conditions were nested in an allOf condition (see the examples below). If an anyOf condition is used, note that the condition skips remaining tests as soon as the first "true" condition is found.

## Example: When, Declarative Pipeline

  ```groovy
     pipeline {
		agent any
		stages {
		  stage('Example Build') {
		    steps {
		    	echo 'Hello World'
			}
		  }
		  stage('Example Deploy') {
		    when {
		      branch 'production'
			  anyOf {
				  environment name: 'DEPLOY_TO', value: 'production'
				  environment name: 'DEPLOY_TO', value: 'staging'
			  }
			}
			steps {
			  	  echo 'Deploying'
			}
		  }
		}
	}
  ```
  See the [When Section in the official Jenkins documentation](https://jenkins.io/doc/book/pipeline/syntax/#when) for its specific usage.