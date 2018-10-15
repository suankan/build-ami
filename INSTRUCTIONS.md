### Part A

Mary from Qantas Loyalty has sent you the following email:

```
Hello!

I have just finished creating a new Ansible role that installs all the packages that the security team and others have asked us for.  I think it would
be a good idea if we created a new Linux AMI that the rest of the team can use as a base for new instances.

Can you please help me create a playbook that starts an ec2 instance, installs the Ansible role and then creates an AMI.

Also, Jeffrey has been talking to me about cost saving so we should think about this when completing this task.

Thanks,

Mary
```

Help Mary by creating a playbook that will create an AMI using the role she has created.

Once you have completed the playbook commit your change and then move on to the next part below.

### Part B

Mary sends you another email:

```
Thank you so much for creating the playbook to create an AMI!

Unfortunately when I ran it it seems there is a problem with my role. When it tries to install the htop package it says something about not being able
to find the package in the repo.  This is strange because I am sure that this package is available in the epel repo.

Can you please have a look?

Thanks,

Mary
```

Take a look at Mary's role 'ql_common_linux'.  Can you suggest a module parameter that might help with her situation?  Make the change and then commit
it and move on to the part step.

### Part C

Mary has one final request:

```
You've been so helpful so far in getting this up and running I wonder if I can ask you one last favor.

Can you please create a new role to set up a website for me?

The website will be 'www.qantastechops.com'.

We would like to apply the role to an ec2 instance that has a public IP addresss and for the role to configure everything we need in order to serve
the site.

Please call the role 'webserver' and place it in the roles directory.

Thanks,

Mary

```

Mary has not specified any particular software to use in order to run the website.  You may choose whatever you are comfortable with.  Include the 
necessary configuration in order to serve the website and anything else you think is necessary.

Make your changes and then commit them.

This is the end of the test.  Push your changes to the origin.

You can now inform your recruiter that you have finished the test.
