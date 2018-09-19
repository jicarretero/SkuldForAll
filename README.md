# SkuldForAll
[![License badge](https://img.shields.io/badge/license-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Prerequistes
You'll need **python-openstackclient** installed so the script can properly work. The script uses python 2.7.

## Description
These are 2 scripts thought to work one after the other. The script **interesting_info.py** will get a lot of information from a FIWARE Openstack node, including users, projects, role_assignments, etc. So an administrator can see a lot of information in a json output.

The output of the file is quite long and it takes some tome to finish, so it is interesting to store that information somewhere to be analized off line. The script takes some time to finish. The way to use this script is running:

    ./interesting_info.py > /tmp/all.json

The file /tmp/all.json can be analyzed later in order to extract the information you need.

There is another script named **get_outdate_people.py**. It will read the file /tmp/all.json and will display the output of the users assigned to projects in a region.

You can change the following lines in order to configure your script:

    REGION = 'Noida'
    JSON_DATA_FILE = '/tmp/all.json'

The first line shows the region you want to query and the second is the json file you want to process.

The output of the file is a set of lines like these, the fields are separated by a white space:

    <type> <user_id> <start_date> <duration> <days_expired> <email> <projects> 


- *type* -- Can be T(trial) or C(community)
- *user_id* -- The user id in Keystone
- *start_date* -- The starting date of the Community or Trial account.
- *duration*  -- The duration of the account. Usually 270 days for community and 15 days for trials.
- *days_expired* -- Days the project has been expired. A negative value means it has not expired yet
- *email*  -- User email
- *projects* -- Number of projects the user belongs to.

