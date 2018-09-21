###about dgraph

 1. 安装dgraph
 `docker pull dgraph/dgraph`
 
 2. 运行docker on linux
 >\# Run Dgraph Zero<br>
 `docker run -it -p 8081:8081 -p 8080:8080 -p 9080:9080 -v ~/dgraph_data:/dgraph --name dgraph dgraph/dgraph dgraph zero --port_offset=-2000`<br>
 \# Run Dgraph Server<br>
`docker exec -it dgraph dgraph server --bindall=true --memory_mb 2048 --zero localhost:5080`<br>
\# Run Dgraph Ratel<br>
`docker exec -it dgraph dgraph-ratel` <br>
 The dgraph server listens on ports 8080 and 9080 with log output to the terminal.<br>
 可在 http://localhost:8081网页中查看UI界面<br>
注意：~/dgraph_data为数据存储的目录，后面接的`：/dgraph`暂时不知道是否需要修改<br>
`--name`后面接的是container的名字，猜测是将第1步pull的dgraph/dgraph命名为~/dgraph_data，后面接的dgraph zero为服务名称，同dgraph server , dgraph-ratel， dgraph live。`-p`为将container内部的端口映射至本机的端口号。
  
 3. 文件的方式导入数据，docker live
 >`docker exec -it dgraph dgraph live -r 1million.rdf.gz --zero localhost:5080`<br>
 >注：1million.rdf.gz为rdf文件，猜测需要压缩为.gz文件。
 
 4. 根据tutorial，导入数据之前貌似需要先将数据的schema导入，具体有待尝试。
 5. 后续需要实现client端口