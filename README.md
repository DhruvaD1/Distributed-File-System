This is a distributed file system that is similar to Hadoop. It is fault tolerant for up to 3 machines. The data replication is done randomly. It uses a master node and multiple data nodes and a client for the user to interact with.


### How to Run
- Install requirements
* run in master server

```
docker pull 33123998/namenode
docker run --rm -i -t -p 2131:2131 33123998/namenode
```
* run in othernode server

```
docker pull 33123998/datanode
docker run --rm -i -t -p 8888:8888 33123998/datanode
``` 
  
### Commands
```sh
Initialize the DFS
$ python3 client.py init block_size replication_Factor

Make new directory in DFS
$ python3 client.py mkdir /dir1/dir2

Remove directory in DFS
$ python3 client.py rmdir /dir1/dir2

List directory in DFS
$ python3 client.py ls /dir1/dir2

Download file from DFS to destination file in local machine
$ python3 client.py read /dir1/file1 dest

Upload file from local machine to DFS
$ python3 client.py write source /dir1/dir2/

Create empty file in DFS with one block size
$ python3 client.py create file /dir1/dir2/

Delete file from DFS
$ python3 client.py delete /dir1/file1

Copy file from one directory to other directory in DFS
$ python3 client.py cp /dir1/file1 /dir1/dir2/file2

Copy file from one directory to other directory in DFS
$ python3 client.py mv /dir1/file1 /dir1/dir2/file2

Metadata of files in DFS
$ python3 client.py info /dir1/file1
