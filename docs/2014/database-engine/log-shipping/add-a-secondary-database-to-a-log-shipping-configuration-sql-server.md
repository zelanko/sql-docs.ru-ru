---
title: Добавление базы данных-получателя в конфигурацию доставки журналов (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 22f1fbc9470eb4002bb40f0e4e513f35134c442e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774365"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a>Добавление базы данных-получателя в конфигурацию доставки журналов (SQL Server)
  В этом разделе объясняется, как добавить базу данных-получатель в имеющуюся конфигурацию доставки журналов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Добавление базы данных-получателя доставки журналов с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для вызова хранимых процедур доставки журналов необходимо членство в предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>Добавление базы данных-получателя доставки журналов  
  
1.  Щелкните правой кнопкой мыши имя базы данных, которая станет базой данных-источником в конфигурации доставки журналов, затем выберите пункт **Свойства**.  
  
2.  В области **Выбор страницы**щелкните **Доставка журналов транзакций**.  
  
3.  В разделе **Экземпляры сервера-получателя и базы данных**нажмите кнопку **Добавить**.  
  
4.  Нажмите **Соединить** и соединитесь с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который нужно использовать в качестве сервера-получателя.  
  
5.  В окне **База данных-получатель** выберите базу данных из списка или введите имя базы данных, которую нужно создать.  
  
6.  На вкладке **Инициализация базы данных-получателя** выберите параметр, который нужно использовать для инициализации базы данных-получателя.  
  
7.  На вкладке **Копирование файлов**введите в поле **Папка назначения для копирования файлов** путь к папке, в которую следует скопировать резервные копии журнала транзакций. Эта папка часто находится на сервере-получателе.  
  
8.  Обратите внимание на расписание копирования в поле **Расписание** в разделе **Задание копирования**. Если необходимо изменить расписание, нажмите кнопку **Расписание** и задайте расписание для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по своему усмотрению. Это расписание должно быть максимально приближено к расписанию резервного копирования.  
  
9. На вкладке **Восстановление журнала транзакций** в разделе **Состояние базы данных во время восстановления резервных копий**выберите пункт **Без режима восстановления** или **Режим ожидания** .  
  
10. Если выбран параметр **Режим ожидания** , то нужно указать, следует ли отключать пользователей от базы данных-получателя, пока идет процесс восстановления.  
  
11. Если нужно отложить процесс восстановления на сервере-получателе, укажите время задержки в поле **Отложить восстановление резервных копий по крайней мере на**.  
  
12. Выберите пороговое значение для предупреждения в поле **Предупреждение, если восстановление не выполнено в течение**.  
  
13. Обратите внимание на расписание восстановления в поле **Расписание** раздела **Задание восстановления**. Если необходимо изменить расписание, нажмите кнопку **Расписание** и задайте расписание для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по своему усмотрению. Это расписание должно быть максимально приближено к расписанию резервного копирования.  
  
14. Нажмите кнопку **ОК**.  
  
15. Чтобы начать процесс настройки, нажмите в диалоговом окне «Свойства базы данных» кнопку **ОК** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>Добавление базы данных-получателя доставки журналов  
  
1.  На сервере-получателе выполните процедуру [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) для обеспечения подробных характеристик сервера-источника и базы данных. Данная хранимая процедура возвращает идентификатор получателя, а также идентификаторы заданий копирования и восстановления.  
  
2.  На сервере-получателе выполните процедуру [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) для настройки расписания заданий копирования и восстановления.  
  
3.  На сервере-получателе выполните процедуру [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) для добавления базы данных-получателя.  
  
4.  На сервере-источнике выполните процедуру [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) для добавления на сервер-источник необходимых сведений о новой базе данных-получателе.  
  
5.  На сервере-получателе включите задания копирования и восстановления. Дополнительные сведения см. в статье [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Обновление доставки журналов до SQL Server 2014 &#40;Transact-SQL&#41;](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Настройка доставки журналов (SQL Server)](configure-log-shipping-sql-server.md)  
  
-   [Удаление базы данных-получателя из конфигурации доставки журналов (SQL Server)](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [Удаление доставки журналов (SQL Server)](remove-log-shipping-sql-server.md)  
  
-   [Просмотр отчета о доставке журналов (среда SQL Server Management Studio)](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Наблюдение за доставкой журналов (Transact-SQL)](monitor-log-shipping-transact-sql.md)  
  
-   [Переход на вторичный сервер доставки журналов (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server &#40;доставки журналов&#41;](about-log-shipping-sql-server.md)   
 [Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md)  
  
  
