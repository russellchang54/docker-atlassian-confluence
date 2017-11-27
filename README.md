基于 https://github.com/cptactionhank/docker-atlassian-confluence 做了破解

//1，启动安装
//2，停止容器，将待破解的包考出
#docker stop confluence
#docker cp confluence:/opt/atlassian/confluence/confluence/WEB-INF/lib/atlassian-extras-decoder-v2-3.2.jar .
//3，将破解包下载到本地，并重名为atlassian-extras-2.4.jar
//4，运行keygen
#java -jar confluence_keygen.jar
//5，先选中atlassian-extras-2.4.jar，执行patch!，生成破解后的atlassian-extras-2.4.jar
//6，再输入name/email/organization/Server ID，执行gen!，生成key
//7，将生成后的atlassian-extras-2.4.jar 复制到容器内
#docker cp atlassian-extras-2.4.jar  confluence:/opt/atlassian/confluence/confluence/WEB-INF/lib/atlassian-extras-decoder-v2-3.2.jar
//8，confluence 的安装界面输入key
//9，启动容器
#docker start confluence
//10，connectionString
jdbc:mysql://clock-builder.com:13306/confluence?useUnicode=true&characterEncoding=utf8&useSSL=false
