---
title: Управление таблицей suspect_pages (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
caps.latest.revision: 54
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e42b62f8732722495337f0ac18de3ddb6acc671a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="manage-the-suspectpages-table-sql-server"></a>Управление таблицей suspect_pages (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается управление таблицей **suspect_pages** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с использованием [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Таблица **suspect_pages** содержит сведения о потенциально поврежденных страницах и используется при принятии решений о необходимости восстановления. Таблица [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md) находится в [базе данных msdb](../../relational-databases/databases/msdb-database.md).  
  
 Страница считается «подозрительной», если при попытке ее чтения компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] обнаруживается одна из следующих ошибок.  
  
-   Ошибка 823, возникающая при проверке циклической контрольной суммы (CRC), запущенной операционной системой, например, ошибка диска (происходит при некоторых ошибках оборудования)  
  
-   Ошибка 824, например разрыв страницы (или любая другая логическая ошибка)  
  
 Идентификатор каждой "подозрительной" страницы записывается в таблицу **suspect_pages** . В эту таблицу [!INCLUDE[ssDE](../../includes/ssde-md.md)] записывает все подозрительные страницы, которые встретились при обработке, в частности:  
  
-   При обработке запроса необходимо считать страницу.  
  
-   При выполнении инструкции DBCC CHECKDB.  
  
-   Во время операции резервного копирования.  
  
 Во время операции восстановления, исправления DBCC или удаления базы данных в случае необходимости также обновляется таблица **suspect_pages** .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Управление таблицей suspect_pages с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   **Ошибки, заносящиеся в таблицу suspect_pages**  
  
     Таблица **suspect_pages** содержит по одной строке на каждую страницу, в которой обнаружена ошибка с номером 824, но не более 1000 строк. В следующей таблице приводятся ошибки, занесенные в столбец **event_type** таблицы **suspect_pages** .  
  
    |Описание ошибки|Значение**event_type** |  
    |-----------------------|---------------------------|  
    |Ошибка 823, вызванная ошибкой CRC операционной системы, или ошибка 824, не относящаяся к неверной контрольной сумме или обрыву страницы (например, неверный идентификатор страницы).|1|  
    |Неверная контрольная сумма|2|  
    |Разрыв страницы|3|  
    |Восстановлена (страница была восстановлена после того, как была помечена поврежденной)|4|  
    |Исправлена (в ходе проверки базы данных DBCC)|5|  
    |Удалена при выполнении DBCC|7|  
  
     В таблицу **suspect_pages** записываются также нерегулярные ошибки.  Их причиной могут быть ошибки ввода-вывода (например отсоединение кабеля) или временно возникшая ошибка проверки контрольной суммы страницы.  
  
-   **Как компонент Database Engine обновляет таблицу suspect_pages**  
  
     Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполняет с таблицей **suspect_pages** следующие действия.  
  
    -   Если таблица не заполнена, она обновляется для каждой ошибки с номером 824 для указания на наличие ошибки; при этом счетчик ошибок увеличивается на единицу. Если страница содержит ошибку, которая впоследствии была исправлена, ее счетчик **number_of_errors** увеличивается на единицу и изменяется значение столбца **last_update** .  
  
    -   После того как указанная страница исправлена операцией восстановления или исправления, в соответствующей строке обновляется столбец **suspect_pages** , указывая, что страница исправлена (**event_type** = 5) или восстановлена (**event_type** = 4).  
  
    -   В ходе проверки базы данных (DBCC) все страницы, не содержащие ошибок, помечаются как исправленные (**event_type** = 5) или освобожденные (**event_type** = 7).  
  
-   **Автоматические обновления таблицы suspect_pages**  
  
     Участник зеркального отображения базы данных или реплика группы доступности AlwaysOn обновляет таблицу **suspect_pages** , если попытка чтения страницы из файла данных завершается одной из следующих ошибок.  
  
    -   Ошибка 823, вызываемая ошибкой CRC операционной системы.  
  
    -   Ошибка 824 (логическая ошибка, например разрыв страницы).  
  
     Следующие действия также автоматически обновляют строки в таблице **suspect_pages** .  
  
    -   Инструкция DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS обновляет таблицу **suspect_pages** , отмечая освобождение или исправление каждой страницы.  
  
    -   Операции полного восстановления, восстановления файла или страницы помечают записи для страниц как восстановленные.  
  
     Следующие действия автоматически удаляют строки из таблицы **suspect_pages** .  
  
    -   ALTER DATABASE REMOVE FILE  
  
    -   DROP DATABASE  
  
-   **Задачи обслуживания, выполняемые администратором базы данных**  
  
     За обслуживание таблицы, преимущественно за удаление старых строк, отвечают администраторы базы данных. Размер таблицы **suspect_pages** ограничен, поэтому после того, как она заполнена, новые ошибки в нее не заносятся. Чтобы не допустить переполнения таблицы, администратор базы данных или системный администратор должен вручную удалить из нее старые строки. Поэтому рекомендуется периодически удалять или архивировать строки, у которых **event_type** указывает на восстановление, или строки, значение **last_update** у которых устарело.  
  
     Для наблюдения за ситуацией в таблице "suspect_pages" можно использовать [класс событий Database Suspect Data Page](../../relational-databases/event-classes/database-suspect-data-page-event-class.md). Строки иногда добавляются в таблицу **suspect_pages** из-за временных ошибок. Однако если в таблицу добавляется множество строк, то, скорее всего, проблема существует в подсистеме ввода-вывода. Если было замечено резко возросшее количество строк, добавляемых в систему, то рекомендуется провести диагностику подсистемы ввода-вывода на предмет возможных проблем.  
  
     Администратор базы данных может также вставлять или обновлять записи. Например, обновление строк может оказаться полезным, если администратор базы данных знает, что какая-нибудь из сомнительных страниц на самом деле исправна, но хочет на время сохранить соответствующую запись.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Сведения в таблице **suspect_pages** доступны любому пользователю, имеющему доступ к базе данных **msdb** . Информация в таблице suspect_pages может обновляться любым пользователем, обладающим разрешением UPDATE. Члены предопределенной роли базы данных **db_owner** в **msdb** или предопределенной роли сервера **sysadmin** могут вставлять, обновлять и удалять записи.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-manage-the-suspectpages-table"></a>Управление таблицей suspect_pages  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], разверните его, а затем разверните узел **Базы данных**.  
  
2.  Разверните последовательно узлы **Системные базы данных**, **msdb**, **Таблицы**и **Системные таблицы**.  
  
3.  Разверните узел **dbo.suspect_pages** и щелкните правой кнопкой мыши **Изменить 200 верхних строк**.  
  
4.  В окне запроса измените, обновите или удалите необходимые строки.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-manage-the-suspectpages-table"></a>Управление таблицей suspect_pages  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующие примеры в окно запроса и нажмите кнопку **Выполнить**. В следующем примере продемонстрировано удаление некоторых строк из таблицы `suspect_pages` .  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 В этом примере происходит возврат поврежденных страниц в таблице `suspect_pages` .  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)   
 [Восстановление страниц (SQL Server)](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [suspect_pages (Transact-SQL)](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
    
   
  
  



