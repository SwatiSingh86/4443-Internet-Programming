## Assignment 5 - Creating your database.

### Due Sep 24<sup>th</sup> by 12:00 p.m.


### Step 1 - Get root password

You need to obtain your root password for mysql. If you haven't changed it, then
you should see it right after you log in. If you have changed it, well you can
probably skip a few steps.

![](http://f.cl.ly/items/3y2S3N2j220u1l2U0X1n/ScreenShot.png)

Write it down, or copy paste it somewhere.

### Step 2 - Change root password

Change your mysql root password. This will make it easier to do the next few steps. The easiest way to do this (the only way as of right now) is to do the following:

```
root@MachineName:~# mysql -u root -p
Enter password: (type or paste your password here)
```
------

After you authenticate. You should see:

```
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

-----

- Then run the following SQL command to actually do the password change. 
- Please change `MyNewPass` to YOUR password.

```sql
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
```

Just type `exit` to get out of mysql command line interface.

### Step 3 - Install Phpmyadmin

Enter the following command, and follow the prompts.

```
root@MachineName:~# sudo apt-get install phpmyadmin
```
-----

Choose apache (press space bar). Hit tab, then enter.

```
     ┌──────────────────────────┤ Configuring phpmyadmin ├───────────────────────────┐
     │ Please choose the web server that should be automatically configured to run   │
     │ phpMyAdmin.                                                                   │
     │                                                                               │
     │ Web server to reconfigure automatically:                                      │
     │                                                                               │
     │    [X] apache2                                                                │
     │    [ ] lighttpd                                                               │
     │                                                                               │
     │                                                                               │
     │                                    <Ok>                                       │
     │                                                                               │
     └───────────────────────────────────────────────────────────────────────────────┘
```
-----

Hit tab (choosing Yes), then hit enter.

```
 ┌──────────────────────────────┤ Configuring phpmyadmin ├───────────────────────────────┐
 │                                                                                       │
 │ The phpmyadmin package must have a database installed and configured before it can    │
 │ be used.  This can be optionally handled with dbconfig-common.                        │
 │                                                                                       │
 │ If you are an advanced database administrator and know that you want to perform this  │
 │ configuration manually, or if your database has already been installed and            │
 │ configured, you should refuse this option.  Details on what needs to be done should   │
 │ most likely be provided in /usr/share/doc/phpmyadmin.                                 │
 │                                                                                       │
 │ Otherwise, you should probably choose this option.                                    │
 │                                                                                       │
 │ Configure database for phpmyadmin with dbconfig-common?                               │
 │                                                                                       │
 │                        <Yes>                           <No>                           │
 │                                                                                       │
 └───────────────────────────────────────────────────────────────────────────────────────┘

```
-----

Enter your root mysql password, hit tab, then enter.

```
  ┌──────────────────────────────┤ Configuring phpmyadmin ├──────────────────────────────┐
  │ Please provide the password for the administrative account with which this package   │
  │ should create its MySQL database and user.                                           │
  │                                                                                      │
  │ Password of the database's administrative user:                                      │
  │                                                                                      │
  │ ____________________________________________________________________________________ │
  │                                                                                      │
  │                       <Ok>                           <Cancel>                        │
  │                                                                                      │
  └──────────────────────────────────────────────────────────────────────────────────────┘
```
-----
You could enter a different password here, but stick with your root password, tab, then enter.

```
  ┌──────────────────────────────┤ Configuring phpmyadmin ├──────────────────────────────┐
  │ Please provide a password for phpmyadmin to register with the database server.  If   │
  │ left blank, a random password will be generated.                                     │
  │                                                                                      │
  │ MySQL application password for phpmyadmin:                                           │
  │                                                                                      │
  │ ____________________________________________________________________________________ │
  │                                                                                      │
  │                       <Ok>                           <Cancel>                        │
  │                                                                                      │
  └──────────────────────────────────────────────────────────────────────────────────────┘
```
-----

Repeat with your password one more time, tab, then enter.

```
                           ┌────┤ Configuring phpmyadmin ├─────┐
                           │                                   │
                           │                                   │
                           │ Password confirmation:            │
                           │                                   │
                           │ _________________________________ │
                           │                                   │
                           │      <Ok>          <Cancel>       │
                           │                                   │
                           └───────────────────────────────────┘
```

If no errors, you should be ready for the next step.

-----

### Logging in to Phpmyadmin

Check your installation by going here:

```
http://yourIpAddress/phpmyadmin
```

Now login:

![](http://f.cl.ly/items/2x2o020H1E2T0j0K0t0q/phplogin.png)

### Adding a Database

__(Skip this section, and go to the next. I will leave this here for documentation purposes).__

- Right after you log in, click on the `Databases` button on the menu bar. 
- It will provide a form to create a database.
- Simply put `4443` in the input box, and click create. 
- Don't worry about the `collation`. That's only if you want to change the default character encoding. 

![](http://f.cl.ly/items/2H2W1b033V0P292q0R2W/create_db.png)

### Adding a Project User (+ Database)

- You need to add a user to Mysql that only has privileges to the `4443` database that we created previously. 
- You could log in with your root user, but that's not the "best practice". Creating a user and compartmentalizing them to the `4443` database is much more secure.
- As you can see below, click on (1) the User tab, then (2) Add User.

![](http://f.cl.ly/items/10182l1o3m0A1r2J2w0S/add_user.png)

- PhpMyAdmin was nice enough to give us some options on this page to allow us to create a database right along with the user we are currently creating.
- Use the example below to add a user, as well as create a database of the same name, with privileges granted to the new user for the newly created database.
- You probably need to scroll down a little to see the "Go" button that submits the form.

![](http://f.cl.ly/items/3c1n0L3g0Z3u3a242f2M/add_user2.png)

### Adding The User Table to your database

- No more pictures.
- After you create the `4443` user and database, select the database for use, by clicking on the `4443` link in the left menu bar.
- This will change the menu bar at the top, giving you a "Sql" menu button.
- Click on this button and paste the code below into the sql box. 
- Click "Go" to submit your query, and create + load your table. 

```sql
CREATE TABLE IF NOT EXISTS `Users` (
  `first_name` varchar(32) NOT NULL,
  `last_name` varchar(32) NOT NULL,
  `id` int(6) NOT NULL AUTO_INCREMENT,
  `email` varchar(64) NOT NULL,
  `dob` int(11) NOT NULL,
  `pass` varchar(32) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=latin1 AUTO_INCREMENT=10 ;

--
-- Dumping data for table `Users`
--

INSERT INTO `Users` (`first_name`, `last_name`, `id`, `email`, `dob`, `pass`) VALUES
('Joe', 'Smith', 1, 'joe.smith@google.com', 73737373, '5f4dcc3b5aa765d61d8327deb882cf99'),
('Bob', 'Jones', 2, 'bob.jones@microsoft.com', 848484, '7c6a180b36896a0a8c02787eeafb0e4c'),
('Kim', 'Jung Il', 5, 'kimjungil@evilempire.ko', 28, '4034a346ccee15292d823416f7510a2f'),
('Kim', 'Jung Un', 6, 'kimjungil@evilempire.ko', 28, '4034a346ccee15292d823416f7510a2f'),
('Kim', 'Jung Il', 7, 'kimjungil@evilempire.ko', 28, '4034a346ccee15292d823416f7510a2f'),
('Dammit', 'Janet', 8, 'dammitjanet.com', 0, 'd41d8cd98f00b204e9800998ecf8427e'),
('Dammit', 'Janet', 9, 'dammitjanet.com', 0, 'd41d8cd98f00b204e9800998ecf8427e');
```

### Add griffin as a user

- Create a user called `griffin` and set his password to your "M" number. 
- Make sure user `griffin` has the privileges to access the `4443` database.
- This is how I will grade this assignment. If I can't log in to phpmyadmin, you get a zero.
