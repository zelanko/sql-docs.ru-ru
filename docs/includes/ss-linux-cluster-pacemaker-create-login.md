1. **На всех серверах SQL Server создайте имя для входа на сервер с помощью Pacemaker**. Следующий запрос Transact-SQL создает имя для входа:

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

  При создании группы доступности пользователю Pacemaker потребуются разрешения на изменение, управление и просмотр определения для группы доступности после ее создания, но до того, как в нее будут добавлены узлы.

1. **На всех серверах SQL Server сохраните учетные данные для входа SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
