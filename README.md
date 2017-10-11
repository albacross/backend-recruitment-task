# backend-recruitment-task

## Database

### MySQL
- The schema of the database that will be used throughout the task is as follows(it's taken from [here](https://dev.mysql.com/doc/employee/en/sakila-structure.html)): 

![alt text](https://github.com/albacross/backend-recruitment-task/raw/master/schema.png)

- In order to access the database, use the following credentials:

address:  `recruitment.ctfrlrhi7vyf.eu-west-1.rds.amazonaws.com`

username: `albacross`

password: `albacross`

database: `employees`

port: `3306`

### Elasticsearch 5.2.1

You can install Elasticsearch on your own or use our vagrant image. Please skip below instruction if you want install on your own.

#### Vagrant
1. Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads) `brew cask install virtualbox`
2. Install [Vagrant](https://www.vagrantup.com/downloads.html) `brew cask install vagrant`
3. Install [vagrant-triggers](https://github.com/emyl/vagrant-triggers) plugin `vagrant plugin install vagrant-triggers`

On Max OS 10.11.X vagrant 1.8.4 and VirtualBox 5.1 are incompatible. Please install vagrant 1.8.0 and VirtualBox 5.0.

#### Run elasticsearch
1. In recruitment task directory run `vagrant up` (may take up to 15 minutes the first time)
2. Check localhost:9202. You should see:

![alt text](https://github.com/albacross/backend-recruitment-task/raw/master/es-installed.png)

### Populate Elasticearch 
```
PUT /department/stats/${dept_name}
{
   "stats_per_employee":[
       {
            "id": ${emp_no},
            "clicks": 12,
            "views": 120
       }
    ]
}
```
