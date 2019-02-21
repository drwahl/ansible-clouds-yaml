Deploy a clouds.yaml file to allow interfacing with multiple openstack clouds
and projects.

To configure your clouds.yaml file, a variable called `clouds` must be provided
as follows:

```
  clouds_config: _(this and all sub-items are optional)_
    path: ~/.openstack
    owner: username
    group: groupname
    mode: 755
    become_root: no
  clouds:
    test_cloud_uno:
      url: https://example.com:5000
      project_name: test_project
      username: test_user
      password: not_a_real_password
```

Some additional information can be provided as well, such as the user and
project domain and the indentity API version.  A successful usecase for this
role has been to create a templated `clouds` variable in `group_vars/all.yaml`
and allow users to create a `host_vars/localhost.yaml` file with additional
information specific to that user (localhost.yaml added to .gitignore). This
allows for centralized management of global things like auth_url while still
giving users the ability to use this role and keep their username and password
out of the git repository.
