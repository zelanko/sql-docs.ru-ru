---
title: "Удаление базы данных-получателя из конфигурации доставки журналов (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "удаление баз данных-получателей"
  - "базы данных-получатели [SQL Server], в доставке журналов"
  - "удаление баз данных-получателей"
  - "вторичные файлы данных [SQL Server], удаление"
  - "доставка журналов [SQL Server], базы данных-получатели"
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
caps.latest.revision: 19
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 19
---
# Удаление базы данных-получателя из конфигурации доставки журналов (SQL Server)
  В этом разделе описывается удаление базы данных-получателя доставки журналов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Удаление базы данных-получателя доставки журналов с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для вызова хранимых процедур доставки журналов необходимо членство в предопределенной роли сервера **sysadmin**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Удаление базы данных-получателя доставки журналов  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который в данный момент является сервером-источником доставки журналов и разверните этот экземпляр.  
  
2.  Разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных-источник доставки журналов и выберите пункт **Свойства**.  
  
3.  В области **Выбор страницы**щелкните **Доставка журналов транзакций**.  
  
4.  В меню **Экземпляры сервера-получателя и базы данных**щелкните базу данных, которую необходимо удалить.  
  
5.  Щелкните **Удалить**.  
  
6.  Нажмите кнопку **ОК** , чтобы обновить конфигурацию.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Удаление базы данных-получатель  
  
1.  Чтобы удалить сведения о базе данных-получателе с сервера-источника, запустите на нем хранимую процедуру [sp_delete_log_shipping_primary_secondary](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql.md).  
  
2.  Чтобы удалить базу данных-получатель с сервера-получателя, запустите на нем хранимую процедуру [sp_delete_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md).  
  
    > [!NOTE]  
    >  Если других баз данных-получателей с таким же идентификатором получателя нет, процедура **sp_delete_log_shipping_secondary_primary** запускается из процедуры **sp_delete_log_shipping_secondary_database** и удаляет запись об идентификаторе получателя, а также задания копирования и восстановления.  
  
3.  На сервере-получателе отключите задания копирования и восстановления. Дополнительные сведения см. в статье [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Обновление доставки журналов до SQL Server 2016 (Transact-SQL)](../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Настройка доставки журналов (SQL Server)](../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
-   [Добавление базы данных-получателя в конфигурацию доставки журналов (SQL Server)](../../database-engine/log-shipping/add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [Удаление доставки журналов (SQL Server)](../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   [Просмотр отчета о доставке журналов (среда SQL Server Management Studio)](../../database-engine/log-shipping/view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Наблюдение за доставкой журналов (Transact-SQL)](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)  
  
-   [Переход на вторичный сервер доставки журналов (SQL Server)](../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Таблицы доставки журналов и хранимые процедуры](../../database-engine/log-shipping/log-shipping-tables-and-stored-procedures.md)  
  
  