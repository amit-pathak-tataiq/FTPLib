# FTP_Lib - FTP & SFTP protocol client

The `FTP_Lib` is built on top of `pysftp` and `ftplib` library. It provides methods to connect to the server and perform upload, download, move and other operations on the server through local machine.

> ## class FTP_Lib(host, user, password=None, server='ftp')

**Parameters:**

`host`: _str_
    
The hostname of the server that needs to be connected. It can either be FTP or SFTP server host.

`user`: _str_

Username of the user that needs to be connected to the server.

`password`: _str, default = None_

Password for the username to be connected to the server. By default, it is None. If it is not provided than the password input is prompted.

`server`: _str, default = 'ftp'_

Server type. One of 'ftp' or 'sftp'.

```python
sftp = FTP_Lib(
    host     = '127.0.0.1',
    user     = 'amit.pathak',
    password = 'password',
    server   = 'sftp'
)
```

### Class Methods

> ## close()

Closes the current server connection.

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.close()
```

> ## ls(remote_path)

Returns the list of files present in the `remote_path` directory of the server.

**Parameters:**

`remote_path` : _str_
    
The directory on the server to look for files and directory.

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.ls(remote_path = "/home")
... ['.bin', 'logs', 'usr', 'version.txt', 'Summer.jpg']
```

> ## pwd()

Returns the current working directory.

```bash
>>> ftp = FTP_Lib(...)
>>> ftp.pwd()
... '/home/logs'
```

> ## cwd(remote_path)

Server path to set the current working directory to.

**Parameters:**

`remote_path`: _str_

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.cwd(remote_path = '/home/usr')
```

> ## rename(remote_src, remote_dest)

Rename a file or directory on the remote host.

**Parameters:**

`remote_src`: _str_

The remote file/directory to rename.

`remote_dest`: _str_

The remote file/directory to put it.

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.rename(remote_src = '/home/Summer.jpg', remote_dest = '/home/Autumn.jpg')
```

> ## download(remote_file, local_dir)

Download the remote file from the server to local system.

**Parameters:**

`remote_file` : _str_

Name of the file with extension and path on the server to be downloaded.

`local_dir` : _str_

The local directory where the file will be downloaded.

```bash
>>> sftp = FTP_Lib(...)
>>> import os
>>> sftp.rename(remote_file = '/home/version.txt', local_dir = os.getcwd())
```

> ## upload(local_file, remote_dir)

Upload the local file to the server.

**Parameters:**

`local_file` : _str_

Name of the local file along with the path to be uploaded.

`remote_dir` : _str_

The directory on the server where the requested file needs to be placed.

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.upload(local_file = 'sample.txt', remote_dir = '/home/')
```

> ## move(remote_src, remote_dest)

Moves a file from one directory to another in the server.

**Parameters:**

`remote_src` : _str_

The current filepath on the server along with the file extension that needs to be moved.

`remote_dest` : _str_

The new filepath with the extension where the file needs to be moved on the server.

```bash
>>> sftp = FTP_Lib(...)
>>> sftp.move(remote_src = 'version.txt', remote_dest = '/home/usr/version.txt')
```
