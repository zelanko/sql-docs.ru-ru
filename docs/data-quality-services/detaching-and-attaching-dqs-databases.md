---
title: Присоединение и отсоединение баз данных DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
author: lrtoyou1223
ms.author: lle
manager: jroth
ms.openlocfilehash: c4f56ac8334be617e800c388158074f801f4aa98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66777704"
---
# <a name="detaching-and-attaching-dqs-databases"></a>Присоединение и отсоединение баз данных DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описывается, как отсоединять и присоединять базы данных DQS.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Limitations"></a> Ограничения  
 Список ограничений см. в статье [Присоединение и отсоединение базы данных (SQL Server)](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Убедитесь, что не существует текущих операций или процессов в DQS. Это можно проверить с помощью экрана **Мониторинг активности** . Дополнительные сведения о работе с этим экраном см. в разделе [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Убедитесь, что на сервере [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]нет подключенных пользователей.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Для отсоединения баз данных DQS учетная запись пользователя Windows должна входить в предопределенную роль сервера db_owner на экземпляре SQL Server.  
  
-   Для присоединения баз данных учетная запись пользователя Windows должна обладать разрешением CREATE DATABASE, CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
-   Для завершения любых выполняемых операций или остановки каких-либо процессов в службах DQS необходимо быть членом роли dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Detach"></a> Отсоединение баз данных DQS  
 При отсоединении базы данных DQS с помощью среды SQL Server Management Studio отсоединенные файлы остаются на компьютере, их можно повторно присоединить к этому же экземпляру SQL Server либо они могу быть перемещены на другой сервер и присоединены там. Файлы баз данных DQS обычно находятся в следующем расположении на компьютере служб Data Quality Services: C:\Program Files\Microsoft SQL Server\MSSQL13. *<Имя_экземпляра>* \MSSQL\DATA.  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов разверните узел **Базы данных** .  
  
3.  Щелкните правой кнопкой мыши базу данных **DQS_MAIN** , укажите пункт **Задачи**, а затем выберите команду **Отсоединить**. Появится диалоговое окно **Отсоединение базы данных** .  
  
4.  Установите флажок в столбце **Удаление** и нажмите кнопку **ОК** , чтобы отсоединить базу данных DQS_MAIN.  
  
5.  Повторите шаги 3 и 4 для баз данных DQS_PROJECTS и DQS_STAGING_DATA, чтобы отсоединить их.  
  
 Базы данных DQS также можно отсоединять с использованием инструкций Transact-SQL с помощью хранимой процедуры sp_detach_db. Дополнительные сведения об отсоединении баз данных с помощью инструкций Transact-SQL см. в подразделе [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) раздела [Detach a Database](../relational-databases/databases/detach-a-database.md).  
  
##  <a name="Attach"></a> Присоединение баз данных DQS  
 Используйте следующие указания для присоединения базы данных DQS к тому же экземпляру SQL Server (от которого она была отсоединена) или другому экземпляру SQL Server, на котором установлен [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] .  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши **Базы данных**и выберите пункт **Присоединить**. Появится диалоговое окно **Присоединение базы данных** .  
  
3.  Чтобы указать базу данных для присоединения, щелкните **Добавить**. Откроется диалоговое окно **Расположение файлов базы данных** .  
  
4.  Выберите диск, на котором находится база данных, и разверните дерево каталогов, чтобы найти и выделить MDF-файл базы данных. Например, для базы данных DQS_MAIN:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  Панель **Сведения базы данных** (внизу) отображает имя присоединяемых файлов. Чтобы проверить или изменить путь к файлу, нажмите кнопку **Обзор** (…).  
  
6.  Чтобы присоединить базу данных DQS_MAIN, нажмите кнопку **ОК** .  
  
7.  Повторите шаги с 2 по 6 для баз данных DQS_PROJECTS и DQS_STAGING_DATA, чтобы присоединить их.  
  
8.  Затем также необходимо выполнить инструкции Transact-SQL после восстановления базы данных DQS_MAIN из копии, в противном случае при попытке подключиться к серверу Data Quality Server с помощью приложения Data Quality Client на экране появится сообщение об ошибке и подключение установить не удастся. Однако выполнять шаги 9 и 10 не требуется, если вы присоединили только базу данных DQS_PROJECTS или DQS_STAGING_DATA, а не базу данных DQS_MAIN.  
  
     Чтобы выполнить инструкции Transact-SQL, в обозревателе объектов щелкните сервер правой кнопкой мыши и выберите команду **Создать запрос**.  
  
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
  
 Базы данных DQS также можно присоединять с помощью инструкций Transact-SQL. Дополнительные сведения о присоединении баз данных с помощью инструкций Transact-SQL см. в подразделе [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) раздела [Attach a Database](../relational-databases/databases/attach-a-database.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление базами данных DQS](../data-quality-services/manage-dqs-databases.md)  
  
  
