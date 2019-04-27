---
title: Удаление базы данных-получателя из конфигурации доставки журналов (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0849d4e10df746dd98e271bb3eb35696cb20337b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774828"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a>Удаление базы данных-получателя из конфигурации доставки журналов (SQL Server)
  В этом разделе описывается удаление базы данных-получателя доставки журналов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Удаление базы данных-получателя доставки журналов с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для вызова хранимых процедур доставки журналов необходимо членство в предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a>Удаление базы данных-получателя доставки журналов  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который в данный момент является сервером-источником доставки журналов и разверните этот экземпляр.  
  
2.  Разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных-источник доставки журналов и выберите пункт **Свойства**.  
  
3.  В области **Выбор страницы**щелкните **Доставка журналов транзакций**.  
  
4.  В меню **Экземпляры сервера-получателя и базы данных**щелкните базу данных, которую необходимо удалить.  
  
5.  Щелкните **Удалить**.  
  
6.  Нажмите кнопку **ОК** , чтобы обновить конфигурацию.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-remove-a-secondary-database"></a>Удаление базы данных-получатель  
  
1.  Чтобы удалить сведения о базе данных-получателе с сервера-источника, запустите на нем хранимую процедуру [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) .  
  
2.  Чтобы удалить базу данных-получатель с сервера-получателя, запустите на нем хранимую процедуру [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) .  
  
    > [!NOTE]  
    >  Если других баз данных-получателей с таким же идентификатором получателя нет, процедура **sp_delete_log_shipping_secondary_primary** запускается из процедуры **sp_delete_log_shipping_secondary_database** и удаляет запись об идентификаторе получателя, а также задания копирования и восстановления.  
  
3.  На сервере-получателе отключите задания копирования и восстановления. Дополнительные сведения см. в статье [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Обновление доставки журналов до SQL Server 2014 &#40;Transact-SQL&#41;](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Настройка доставки журналов (SQL Server)](configure-log-shipping-sql-server.md)  
  
-   [Добавление базы данных-получателя в конфигурацию доставки журналов (SQL Server)](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [Удаление доставки журналов (SQL Server)](remove-log-shipping-sql-server.md)  
  
-   [Просмотр отчета о доставке журналов (среда SQL Server Management Studio)](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Наблюдение за доставкой журналов (Transact-SQL)](monitor-log-shipping-transact-sql.md)  
  
-   [Переход на вторичный сервер доставки журналов (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Сведения о доставке журналов (SQL Server)](about-log-shipping-sql-server.md)   
 [Таблицы доставки журналов и хранимые процедуры](log-shipping-tables-and-stored-procedures.md)  
  
  
