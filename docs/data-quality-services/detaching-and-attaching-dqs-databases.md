---
title: "Присоединение и отсоединение баз данных DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Присоединение и отсоединение баз данных DQS
  В этом разделе описывается, как отсоединять и присоединять базы данных DQS.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Limitations"></a> Ограничения  
 Список ограничений, см. в разделе [Отсоединение базы данных и присоединить & #40; SQL Server & #41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Убедитесь, что не существует текущих операций или процессов в DQS. Это можно проверить с помощью экрана **Мониторинг активности** . Дополнительные сведения о работе с этим экраном см. в разделе [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Убедитесь, что на сервере [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]нет подключенных пользователей.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
  
-   Для отсоединения баз данных DQS учетная запись пользователя Windows должна входить в предопределенную роль сервера db_owner на экземпляре SQL Server.  
  
-   Для присоединения баз данных учетная запись пользователя Windows должна обладать разрешением CREATE DATABASE, CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
-   Для завершения любых выполняемых операций или остановки каких-либо процессов в службах DQS необходимо быть членом роли dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Detach"></a> Отсоединение баз данных DQS  
 При отсоединении базы данных DQS с помощью среды SQL Server Management Studio отсоединенные файлы остаются на компьютере, их можно повторно присоединить к этому же экземпляру SQL Server либо они могу быть перемещены на другой сервер и присоединены там. Файлы базы данных DQS обычно находятся в следующей папке на компьютере служб качества данных: C:\Program Files\Microsoft SQL Server\MSSQL13.*\< Имя_экземпляра >*\MSSQL\DATA.  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов разверните узел **Базы данных** .  
  
3.  Щелкните правой кнопкой мыши **DQS_MAIN** базы данных, выберите пункт **задачи**, а затем нажмите кнопку **отсоединения**. Появится диалоговое окно **Отсоединение базы данных** .  
  
4.  Установите флажок в группе **Drop** столбец и нажмите кнопку **ОК** отсоединить базу данных DQS_MAIN.  
  
5.  Повторите шаги 3 и 4 для баз данных DQS_PROJECTS и DQS_STAGING_DATA, чтобы отсоединить их.  
  
 Базы данных DQS также можно отсоединять с использованием инструкций Transact-SQL с помощью хранимой процедуры sp_detach_db. Дополнительные сведения об отсоединении баз данных с помощью инструкций Transact-SQL см. в разделе [с помощью Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) в [отсоединения базы данных](../relational-databases/databases/detach-a-database.md).  
  
##  <a name="Attach"></a> Присоединение баз данных DQS  
 Используйте следующие указания для присоединения базы данных DQS к тому же экземпляру SQL Server (от которого она была отсоединена) или другому экземпляру SQL Server, на котором установлен [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши **базы данных**, а затем нажмите кнопку **присоединить**. Появится диалоговое окно **Присоединение базы данных** .  
  
3.  Чтобы указать базу данных для присоединения, щелкните **Добавить**. Откроется диалоговое окно **Расположение файлов базы данных** .  
  
4.  Выберите диск, на котором находится база данных, и разверните дерево каталогов, чтобы найти и выделить MDF-файл базы данных. Например, для базы данных DQS_MAIN:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.   **Сведения о базе данных** (нижней) отображает имена файлов для вложения. Чтобы проверить или изменить путь к файлу, нажмите кнопку **Обзор** кнопку (...).  
  
6.  Щелкните **ОК** для присоединения базы данных DQS_MAIN.  
  
7.  Повторите шаги с 2 по 6 для баз данных DQS_PROJECTS и DQS_STAGING_DATA, чтобы присоединить их.  
  
8.  Затем также необходимо выполнить инструкции Transact-SQL после восстановления базы данных DQS_MAIN из копии, в противном случае при попытке подключиться к серверу Data Quality Server с помощью приложения Data Quality Client на экране появится сообщение об ошибке и подключение установить не удастся. Однако выполнять шаги 9 и 10 не требуется, если вы присоединили только базу данных DQS_PROJECTS или DQS_STAGING_DATA, а не базу данных DQS_MAIN.  
  
     Чтобы выполнить инструкции Transact-SQL, в обозревателе объектов, щелкните правой кнопкой мыши сервер и нажмите кнопку **новый запрос**.  
  
9. В окно редактора запросов скопируйте следующие инструкции SQL:  
  
    ```  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
  
    ```  
  
10. Нажмите клавишу F5, чтобы выполнить инструкции. Откройте область «Результаты», чтобы удостовериться в успешном выполнении инструкций. На экране появится следующее сообщение: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`  
  
11. Подключитесь к серверу Data Quality Server с помощью приложения Data Quality Client, чтобы проверить возможность установления подключения.  
  
 Базы данных DQS также можно присоединять с помощью инструкций Transact-SQL. Дополнительные сведения о присоединении баз данных с помощью инструкций Transact-SQL см. в разделе [с помощью Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) в [подключить базу данных](../relational-databases/databases/attach-a-database.md).  
  
## См. также:  
 [Управление базами данных DQS](../data-quality-services/manage-dqs-databases.md)  
  
  