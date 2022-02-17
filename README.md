# FTP_Lib - FTP & SFTP protocol client

The `FTP_Lib` is built on top of `pysftp` and `ftplib` library. It provides methods to connect to the server and perform upload, download, move and other operations on the server through local machine.

> ## class FTP_Lib(host, user, password=None, server='ftp')


**Parameters:**

`host`: _str_
    
The hostname of the server that needs to be connected. It can either FTP or SFTP server host.

`user`: _str_

    Username of the user that needs to be connected to the server.

`password`: _str, default = None_

    Password for the username to be connected to the server. By default, it is None. If it is not provided than the password input is prompted.

`server`: _str, default = 'ftp'_

    Server type. One of 'ftp' or 'sftp'.


### Class Methods

> ## close()

Closes the current server connection.

> ## ls()

Returns the list of files present in the `remote_path` directory of the server.

`remote_path` : _str_
    
    The directory on the server to look for.
