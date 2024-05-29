
This is a distributed file system similar to HDFS. It has one Master (NameNode) and multiple Storages (DataNode), as well as a client for interaction. When given a SIGINT, it will dump the namespace information (dir_tree and file_tree) and reload it when fired up next time (fs.img). Data replication is done randomly, similar to HDFS. The data is sent to the first storage, which then sends it to the next one and so on. Reading is done in a similar manner - it will contact the first storage for the block, and if it fails, it will try the second and so on. This system uses the RPyC library in Python for RPC.

This is a distributed file system that is similar to Hadoop. It is fault tolerant for up to 3 machines. The data replication is done randomly. It uses a master node and multiple data nodes and a client for the user to interact with.


### How to Run
- Install requirements
* run in namenode server

```
docker pull 33123998/namenode
docker run --rm -i -t -p 2131:2131 33123998/namenode
```
* run in datanode server

```
docker pull 33123998/datanode
docker run --rm -i -t -p 8888:8888 33123998/datanode
``` 
  
### Example Commands
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
