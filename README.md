# Docker Commands

### Failing For Any Module or Adding any New Changes (In backend requirements.txt or frontend package.json changes)
`docker build . -t wsgi:bodhitree3`

### Removing Docker Stack and Redeploying 
`docker stack rm bodhi_demo`
`docker stack deploy -c docker-compose.dev.yml bodhi_demo` 

Preferred : 
`docker service update bodhi_robin_test_wsgi --force`

### Removing Stopped Container, Unused Networks, Dangling Images and Build Cache
`docker system prune`

# Mongo Setup Using Docker 

 

Once inside container need permissions use this. 
See the docker file for configuration
mongo -u <username> -p <password> --authenticationDatabase <auth_db>
mongosh -u root -p example --authenticationDatabase admin

show dbs

use your_database_name

db.dropDatabase()

db.getCollection("dump_data_criteria")

db.dump_data_criteria.find({ title: "Functionality" }).pretty()

db.dump_data_criteria.find().pretty()



## How to list problem on the basis of problem id ?
`
problem = Problem.objects.filter(problem_id=123).first()

                            if problem:
                                # Print Problem details
                                print(f"Problem ID: {problem.problem_id}")
                                print(f"Problem Statement: {problem.problem_statement}")
                                print(f"User ID: {problem.user_id}")
                                
                                # Fetch and print related Criteria
                                criteria_list = problem.criteria.all()
                                print("Associated Criteria:")
                                for criteria in criteria_list:
                                    print(f"  Criteria ID: {criteria.criteria_id}")
                                    print(f"  Title: {criteria.title}")
                                    print(f"  Description: {criteria.description}")
                                    print(f"  Rating ID: {criteria.rating.id}")
                                    print("  ------------------------")
                            else:
                                print(f"No Problem found with problem_id={problem_id}")
                                
## One to One vs Foreign 
'''Using OneToOneField: If you set criteria or submission as a OneToOneField, the GradingHistory can only link to a Criteria record if there is a unique one-to-one relationship. This means each Criteria can only appear once in GradingHistory, and queries might not work as expected if multiple GradingHistory records are linked to the same Criteria.'''


`
