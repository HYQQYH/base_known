###about dgraph

 1. 安装dgraph
 `docker pull dgraph/dgraph`
 
 2. 运行docker on linux
 >\# Run Dgraph Zero
 `docker run -it -p 8080:8080 -p 9080:9080 -p 8081:8081 -v /tmp/data:/dgraph --name diggy dgraph/dgraph dgraph zero --port_offset -2000`
 \# Run Dgraph Server
`docker exec -it diggy dgraph server --memory_mb 2048 --zero localhost:5080`
\# Run Dgraph Ratel
`docker exec -it diggy dgraph-ratel` 
 The dgraph server listens on ports 8080 and 9080 with log output to the terminal.
 可在 http://localhost:8081网页中查看UI界面
注意：/tmp/data为数据存储的目录，后面接的`：/dgraph`暂时不知道是否需要修改
`--name`后面接的是container的名字，猜测是将第1步pull的dgraph/dgraph命名为diggy，后面接的dgraph zero为服务名称，同dgraph server , dgraph-ratel， dgraph live。`-p`为将container内部的端口映射至本机的端口号。
  
 3. 文件的方式导入数据，docker live
 >`docker exec -it diggy dgraph live -r 1million.rdf.gz --zero localhost:5080`
 >注：1million.rdf.gz为rdf文件，猜测需要压缩为.gz文件。
 
 4. 根据tutorial，导入数据之前貌似需要先将数据的schema导入，具体有待尝试。
 5. 后续需要实现client端口