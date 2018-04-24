---
title: Восстановление разностной резервной копии базы данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
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
- full differential backups [SQL Server]
- restoring databases [SQL Server], full differential backups
- database backups [SQL Server], full differential backups
- database restores [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
ms.assetid: 0dd971a4-ee38-4dd3-9f30-ef77fc58dd11
caps.latest.revision: 46
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b466775d401b1180859eef9d14e7afc0eff6d1fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="restore-a-differential-database-backup-sql-server"></a>Восстановление разностной резервной копии базы данных (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описано, как восстановить разностную резервную копию базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [безопасность](#Security)  
  
-   **Восстановление разностной резервной копии базы данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Инструкция RESTORE недопустима в явной или неявной транзакции.  
  
-   Резервные копии, созданные более поздними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не могут быть восстановлены в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]можно восстановить пользовательскую базу данных из резервной копии базы данных, созданной с помощью [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Перед восстановлением базы данных в среде по модели полного восстановления или модели восстановления с неполным протоколированием необходимо выполнить резервное копирование активного журнала транзакций (который называется заключительным фрагментом журнала). Дополнительные сведения см. в статье [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-restore-a-differential-database-backup"></a>Восстановление разностной резервной копии базы данных  
  
1.  После подключения к соответствующему экземпляру компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в обозревателе объектов разверните дерево сервера, щелкнув имя сервера.  
  
2.  Разверните узел **Базы данных**. В зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных**и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, затем пункт **Восстановить**и пункт **База данных**.  
  
4.  Чтобы указать источник и расположение восстанавливаемых резервных наборов данных, используйте страницу **Общие** , раздел **Источник** . Выберите один из следующих вариантов.  
  
    -   **База данных**  
  
         Выберите из раскрывающегося списка базу данных для восстановления. Данный список содержит только базы данных, резервное копирование которых было выполнено в соответствии с журналом резервного копирования **msdb** .  
  
    > [!NOTE]  
    >  Если резервная копия была получена с другого сервера, на целевом сервере не будет журнала резервного копирования для указанной базы данных. В этом случае щелкните пункт **Устройство** , чтобы вручную указать файл или устройство для восстановления.  
  
    -   **Устройство**  
  
         Нажмите кнопку обзора (**...**), после чего откроется диалоговое окно **Выбор устройств резервного копирования** . В окне **Тип носителя резервной копии** выберите один из перечисленных типов устройств. Чтобы выбрать одно или несколько устройств в окне **Носитель резервной копии** , нажмите кнопку **Добавить**.  
  
         После добавления нужных устройств в списке **Носитель резервной копии** нажмите кнопку **ОК** для возвращения на страницу **Общие** .  
  
         В списке **Источник: Устройство: База данных** выберите имя базы данных, которую нужно восстановить.  
  
         **Примечание.** Этот список доступен, только если выбрано **Устройство** . Будут выбраны только те базы данных, резервные копии которых доступны на выбранном устройстве.  
  
5.  В разделе **Назначение** , в поле **База данных** автоматически появится имя базы данных для восстановления. Для изменения имени базы данных введите новое имя в окно **База данных** .  
  
    > [!NOTE]  
    >  Для остановки восстановления на определенный момент времени выберите пункт **Временная шкала** и перейдите в диалоговое окно **Временная шкала резервных копий** . Справочные сведения по остановке восстановления базы данных в определенный момент доступны в разделе [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
6.  В сетке **Резервные наборы данных для восстановления** выберите резервные копии, которые необходимо восстановить с помощью разностного восстановления.  
  
     Сведения о столбцах в сетке **Восстанавливаемые резервные наборы данных** см. в статье [Восстановление базы данных (страница "Общие")](../../relational-databases/backup-restore/restore-database-general-page.md).  
  
7.  На странице **Параметры** используйте панель **Параметры восстановления** для выбора любого из следующих вариантов, если он подходит к данной ситуации.  
  
    -   **Перезаписать существующую базу данных (WITH REPLACE)**  
  
    -   **Сохранить параметры репликации (WITH KEEP_REPLICATION)**  
  
    -   **Выдавать приглашение перед восстановлением каждой резервной копии**  
  
    -   **Ограничить доступ к восстановленной базе данных (WITH RESTRICTED_USER)**  
  
     Дополнительные сведения об этих параметрах см. в статье [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md).  
  
8.  Выберите параметр в поле **Состояние восстановления** . В данном окне определяется состояние базы данных после операции восстановления.  
  
    -   По умолчанию установлена схема**RESTORE WITH RECOVERY** , при этом база данных находится в готовом состоянии для использования путем отката незафиксированных транзакций. Невозможно восстановить дополнительные журналы транзакций. Выберите данный параметр, если выполняется восстановление всех необходимых резервных копий.  
  
    -   Схема**RESTORE WITH NORECOVERY** оставляет базу данных в нерабочем состоянии и не выполняет откат незафиксированных транзакций. Можно восстановить дополнительные журналы транзакций. База данных не может быть использована, пока не будет восстановлена.  
  
    -   Схема**RESTORE WITH STANDBY** оставляет базу данных в режиме только для чтения. С помощью данного параметра можно отменить незафиксированные транзакции и сохранить отмененные действия в резервном файле, чтобы результаты восстановления можно было отменить.  
  
     Описание параметров см. в статье [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md).  
  
9. Если имеются активные соединения с базой данных, операции восстановления завершатся ошибкой. Проверьте окно **Закрыть существующие соединения** и убедитесь, что все активные соединения между [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и базой данных закрыты.  
  
10. Установите флажок **Выдавать запрос перед восстановлением каждой резервной копии** , если хотите отследить каждую операцию восстановления. Обычно это не требуется, за исключением случаев, если необходимо наблюдать за состоянием операции восстановления базы данных большого объема.  
  
11. По желанию можно использовать страницу **Файлы** для восстановления базы данных в новом расположении. Дополнительные сведения см. в разделе [Восстановление базы данных в новом расположении (SQL Server)](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-restore-a-differential-database-backup"></a>Восстановление разностной резервной копии базы данных  
  
1.  Выполните инструкцию RESTORE DATABASE с предложением NORECOVERY, чтобы восстановить полную резервную копию базы данных, которая предшествует разностной резервной копии базы данных. Дополнительные сведения см. в статье [Практическое руководство. Восстановление полной резервной копии](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md).  
  
2.  Выполните инструкцию RESTORE DATABASE для восстановления разностной резервной копии базы данных, указав:  
  
    -   имя базы данных, к которой будет применена разностная резервная копия;  
  
    -   устройство резервного копирования, с которого происходит восстановление разностной резервной копии базы данных;  
  
    -   предложение NORECOVERY в случае, если нужно применить резервные копии журнала транзакций после восстановления разностной резервной копии базы данных. В противном случае укажите предложение RECOVERY.  
  
3.  В модели полного восстановления или модели восстановления с неполным протоколированием разностная резервная копия восстанавливает базу данных на момент выполнения разностного резервного копирования. Чтобы восстановить данные на момент сбоя, следует применить все резервные копии журнала транзакций, созданные после создания последней разностной копии базы данных. Дополнительные сведения см. в разделе [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
  
#### <a name="a-restoring-a-differential-database-backup"></a>A. Восстановление разностной резервной копии базы данных  
 В этом примере показано восстановление базы данных и разностной резервной копии базы данных `MyAdvWorks` .  
  
```sql  
-- Assume the database is lost, and restore full database,   
-- specifying the original full database backup and NORECOVERY,   
-- which allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   RECOVERY;  
GO  
```  
  
#### <a name="b-restoring-a-database-differential-database-and-transaction-log-backup"></a>Б. Восстановление базы данных, разностной резервной копии базы данных и журнала транзакций  
 В этом примере показано восстановление базы данных, разностной резервной копии базы данных и резервной копии журнала транзакций базы данных `MyAdvWorks` .  
  
```sql  
-- Assume the database is lost at this point. Now restore the full   
-- database. Specify the original full database backup and NORECOVERY.  
-- NORECOVERY allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   NORECOVERY;  
GO  
-- Now restore each transaction log backup created after  
-- the differential database backup.  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log1  
   WITH NORECOVERY;  
GO  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log2  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
