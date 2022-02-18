[Go Back](README.md)

# FTP_Lib [Examples]

**Install Dependencies**
```bash
>>> pip install pysftp
>>> pip install ftplib
```


```python
from FTP_Lib import FTP_Lib
```

## SFTP Server

* Creating connection


```python
sftp = FTP_Lib(
    host   = '127.0.0.1',
    user   = 'amit.pathak',
    server = 'sftp'
)
```

    Enter SFTP PASSWORD : ········
    

* Check current working pwd


```python
sftp.pwd()
```




    '/home/amit.pathak'



* Change current working directory


```python
sftp.cwd(remote_path = '/home/amit.pathak/demo')
sftp.pwd()
```




    '/home/amit.pathak/demo'



* Show files and directories in CWD


```python
sftp.ls()
```




    ['Notes.txt']



* Download File from server to local directory


```python
import os

print("File present before downloading:", 'Notes.txt' in os.listdir())
# --------------------------------------------------------------
sftp.download(
    remote_file = '/home/amit.pathak/demo/Notes.txt',
    local_dir   = os.getcwd()
)
# --------------------------------------------------------------
print("File present after downloading:", 'Notes.txt' in os.listdir())
```

    File present before downloading: True
    File present before downloading: True
    

* Upload file from local system to server


```python
import os

print("File present before uploading:", 'demo.txt' in sftp.ls())
# --------------------------------------------------------------
sftp.upload(
    local_file = os.path.join(os.getcwd(), 'demo.txt'),
    remote_dir = '/home/amit.pathak/demo' # or sftp.pwd()
)
# --------------------------------------------------------------
print("File present after uploading:", 'demo.txt' in sftp.ls())
```

    File present before uploading: False
    File present after uploading: True
    

* Move a file from one location to another in the server


```python
print(sftp.pwd())
print(sftp.ls())
# --------------------------------------------------------------
sftp.move(
    remote_src  = '/home/amit.pathak/demo/Notes.txt',
    remote_dest = '/home/amit.pathak/Notes.txt'
)
# --------------------------------------------------------------
sftp.ls()
```

    /home/amit.pathak/demo
    ['demo.txt']



* Rename a file in the server


```python
sftp.rename(
    remote_src  = '',
    remote_dest = ''
)
```

[Go Back](README.md)
