There are below steps are involved in the building of VM_Reservation_System :

1-When the user runs the script , the script asks for methods as checkout or checkin and on the basis of that it calls the concerned functions.
Now the user can also be pre calculated, (for example) if the script is being run from a Jenkins job, we can use the Jenkins env variable $BUILD_USER_ID, but I am here making it run as a script as the execution env was not mentined and hence asking user to enter the user name explicitly.

I have alearedy attached the csv (vm_list.csv) having all the list of the severs with their current owner which would be created & managed by the VM Administrator. 

2-On the basis of the checkout method given as input, the script checks if there is any server available with column 'Not_allocated' in the csv and shares the first ip address and then changes the 'Not_allocated' value to the "user_name" given while running the script in the CSV.

3-Likewise on the basis of checkin method given as input, the script changes the "current_owner" value from the user name to not 'Not_allocated' in the csv and then ssh to the IP and do the required cleanup activity.


Note: 
As of now, I have kept the CSV generation task as manual as generating it automatically required communicating with a cloud (for example) AWS using the AWS cli and for that it would have required IAM credentials and hence it would not have worked on your machine.

However, I have added the required functions to fetch the list of the servers from AWS and then build the CSV automatically with the data and then push the CSV to the git which could be fetched and used as a dynamic inventory for the script.

I have commented the calls for these functions as it would not work on your machine without the required AWS credentials but wanted to showcase that this is how we can also build the CSV automtically.