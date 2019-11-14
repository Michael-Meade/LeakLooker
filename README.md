In this example, there are 5 users being added to the table. Your query is then run. The expected result would be to return the password value for the admin user only.

However, by adding ```1=1```, which is a true statement, all passwords are returned.

Another way to help visualize this, is to add parenthesis so that you can see how everything is evaluated.

```ruby
SELECT pass FROM users WHERE (user_name = 'admin')              OR (1=1) -- '
                                 ^ Pulls only the admin user        ^ Pulls everything because 1=1
```
So, we are selecting the password from the table where the user name is admin. We are also pulling the password from the table where ever 1=1 - which is always true. Each row is evaluated to true, thus all passwords are returned.

The final ```-- '``` is used to comment out the rest of your query.

```SELECT pass from users WHERE user_name = 'admin' or (1=1) -- 'and permission='superadmin```

Normally, (if the 1=1 hadn't been injected), you'd pull the password for the user with user_name of admin and superadmin permissions. You've now commented that out, and it isn't executed. This is how the entire table of passwords can be returned.
*source: https://stackoverflow.com/questions/24843689/whats-the-meaning-of-admin-or-1-1/24843726* 
