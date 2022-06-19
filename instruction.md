Smoke Testing Jobs
Write a job that performs a smoke test.

Prerequisites
The current exercise is in continuation to the previous Exercise: Config and Deployment.

Instructions
Create a job named smoke_test to do a simple check on a website ("https://blog.udacity.com/") to see if it exists or not. You can do this easily with curl.

If the curl command exits with a non-zero, it means the site had an error. Catch the error and make sure the pipeline fails. Your code will look like:

# Exercise: Smoke Testing
smoke_test:
 docker:
   - image: alpine:latest
 steps:
   - run: apk add --update curl
   - run:
       name: smoke test
       command: |
         URL="https://blog.udacity.com/"
         # Test if website exists
         if curl -s --head ${URL} 
         then
           return 0
         else
           return 1
         fi

Define a workflow that uses the current job. Comment out the other/unnecessary jobs from the workflow.

Push your edits.

Ensure to have the Job build successfully in the CircleCI environment.

If you strongly need help, refer to this file in the Github repo.