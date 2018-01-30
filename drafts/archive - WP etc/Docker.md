"login" into a docker container . It feels like ssh-ing (it's not).

>unsure of the difference between these two commands

`$ docker exec -ti <your_container_name>`
`$ docker exec -t -i <your_container_name> /bin/bash`
