Some mysql notes
----------------
+ create dump
    + `mysqldump -u user -p db > dumpfile.sql`
+ import dump
    + `mysql -u user -p db < dumpfile.sql`
+ table > csv
    + `mysql> select * INTO OUTFILE ‘/tmp/file.out’ from TABLE;`
+ On **ERROR 1045 (28000): Access denied for user 'db_user'@'localhost' (using password: YES)**

    ```
    mysql -u root -p
        1. use mysql;
        2. update user set File_priv = ‘Y’ where User = ‘db_user’;
        3. FLUSH PRIVILEGES;
    ```
