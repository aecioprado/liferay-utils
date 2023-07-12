## Criar um container docker do mysql

```shell
docker run \
        --name mysql \
        -p 3306:3306 \
        -e MYSQL_DATABASE=lportal \
        -e MYSQL_ROOT_PASSWORD=root \
        -d mysql:8.0 \
        --character-set-server=utf8 \
        --collation-server=utf8_general_ci \
        --lower-case-table-names=0
```
## Configurar a conexão com o banco de dados
#### O arquivo de configuração fica na pasta bundles/portal-ext.properties

```properties
include-and-override=portal-developer.properties

#
# MySQL
#
jdbc.default.driverClassName=com.mysql.cj.jdbc.Driver
jdbc.default.url=jdbc:mysql://localhost:3306/lportal-db?useUnicode=true&characterEncoding=UTF-8&useFastDateParsing=false
jdbc.default.username=root
jdbc.default.password=test
```

## Acessar o container mysql

```
docker exec -it mysql  mysql -uroot -p
```
No terminal informar a senha criada anteriomente

## Mudança de senha
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
```
