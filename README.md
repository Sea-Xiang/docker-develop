# 环境启动步骤
> 1. 创建网络：docker network create hyperf_net
> 2. 验证网络：docker network ls | grep hyperf_net
> 3. 启动环境：docker compose up -d --build

# 项目代码路径
> 当前目录的上一级，例：`../demo`，一个项目一个目录

# 目录结构说明
```text
└── conf                       # 配置文件目录
    ├── mysql   
    │   └── my.conf             
    ├── nginx   
    │   ├── conf.d                
    │   ├── local.demo.conf                 
    │   └── nginx.conf                       
    ├── php7.3
    │   ├── php.ini   
    │   ├── php-fpm.conf   
    │   └── yaf.ini   
    ├── php7.4
    │   ├── php.ini           
    │   ├── php-fpm.conf        
    │   └── yaf.ini             
    ├── php8.3
    │   ├── php.ini   
    │   ├── php-fpm.conf   
    │   └── yaf.ini   
└── data                       # 数据文件目录
    ├── mysql
    ├── es
    └── redis    
└── fpm.7.3                    # PHP7.3 FPM 镜像构建目录
    └── Dockerfile
└── fpm.7.4                    # PHP7.4 FPM 镜像构建目录
    └── Dockerfile
└── fpm.8.3                    # PHP8.3 FPM 镜像构建目录
    └── Dockerfile
└── logs                       # 日志文件目录
    ├── mysql
    ├── nginx
    └── fpm7.3
    └── fpm7.4
    └── fpm8.3
└── docker-compose.yml         # Docker Compose 配置文件
```