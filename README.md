NOTES
=====

`login_db`
specifies which database Ansible connects to in order to execute the SQL command that creates or updates the user account. It has no effect on user permissions or database ownership.

1. Create the User (community.postgresql.postgresql_user)
2. Create the Database and assign Ownership (community.postgresql.postgresql_db)

Passwordless management
-----------------------

By default, PostgreSQL uses peer authentication for local Unix domain socket connections.
PostgreSQL checks the system user making the socket connection. 
If it matches the database user postgres, access is granted immediately—no password required.

To avoid “Peer authentication failed for user postgres” error, use postgres user as a `become_user`.