# rhcp.user Collection

Collection containing roles to manage users on the Red Hat customer portal

# Roles

## `rhcp.user.get_access_token`
 
Uses the offline token passed in as a variable to retrieve an access token and sets a fact with the value. invoked by `create_user`

## `rhcp.user.get_account_id`
 
retrieves the account id for the token and sets a fact with the value. invoked by `create_user`

## `rhcp.user.create_user`

Create a user based on the information passed in through extra vars. All values have defaults defined, and the default values are:
```
username: "ansible_demo_user"
email: "ansoble_demo_user@redhat.com"
salutation: "Mr."
firstName: "Ansible"
lastName: "User"
phone: "5555555555"
address_city: "Raleigh"
address_country: "US"
address_county: "Wake"
address_state: "NC"
address_street: "100 E Davie St"
address_zipcode: "27601"
```

# Usage

sample playbook to create a user

```
--- 
- name: Create a new user
  hosts: localhost
  gather_facts: no
  vars:
    offline_token: <YOUR TOKEN GOES HERE>
    username: "ansible_demo_user"
    email: "ansible_demo_user@redhat.com"
    salutation: "Mr."
    firstName: "Ansible"
    lastName: "User"
    phone: "5555555555"
    address_city: "Raleigh"
    address_country: "US"
    address_county: "Wake"
    address_state: "NC"
    address_street: "100 E Davie St"
    address_zipcode: "27601"
  roles:
  - rhcp.user.create_user
```