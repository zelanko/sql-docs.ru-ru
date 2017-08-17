1. **На всех серверах SQL Server создайте имя для входа на сервер с помощью Pacemaker**. Следующий запрос Transact-SQL создает имя для входа:

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

   Вы также можете задать разрешения на более детальном уровне. Имени для входа Pacemaker требуются разрешения на изменение, управление и просмотр определения для управления группой доступности, а также разрешение на просмотр состояния сервера для запуска sp_server_diagnostics. Дополнительные сведения см. в статьях [GRANT (предоставление) разрешений группы доступности (Transact-SQL)](http://msdn.microsoft.com/library/hh968934.aspx) и [Разрешения sp_server_diagnostic](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql#permissions).

   Следующий запрос Transact-SQL предоставляет только разрешения, необходимые для входа с помощью Pacemaker. В приведенной ниже инструкции ag1 — это имя группы доступности, которая будет добавлена в качестве ресурса кластера.

   ```Transact-SQL
   GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO pacemakerLogin
   GRANT VIEW SERVER STATE TO pacemakerLogin
   ```

1. **На всех серверах SQL Server сохраните учетные данные для входа SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
