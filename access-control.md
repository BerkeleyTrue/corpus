---
title: access control
---

## Access control

* There are two types of control models
  * Role Based Access Control (RBAC)
  * Discretionary Based Access Control (DAC)

### RBAC

* provides mandatory access control (MAC) concept
  * you do not assign yourself or others to a role. A role admin or engineer
      does that
* elements created for this role can not be accessed by somone who does not act
    under that role
* provides the idea of mutually exclusive roles
* helps you manage permissions
* think of roles as `context`
  * a role X describes a security context that dictates how subject Y can access
      (or not) a object Z
* role admins are in charge of giving roles to subjects
* role engineers are in charge of creating roles/permissions
* roles are the 'Why'. They ask questions, they don't anser

### DAC (groups)

* permissions are purely additive
* helps you manage objects and subjects
* groups answer the question 'What'. they are the 'is'. Subject A 'is' a dev
    (group)

### Groups vs Roles

* A group is a means of organising users, whereas a role is usually a means of organising rights (permissions).


#### links

[role/group](https://profsandhu.com/workshop/role-group.pdf)
