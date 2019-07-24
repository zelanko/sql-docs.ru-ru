---
title: Восстановление базы данных в новое место (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bef38ae0b93eb43d508192c6f748a36320143689
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937537"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a>Восстановление базы данных в новое место (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как восстановить базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в новую папку и при необходимости переименовать ее в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью SQL Server Management Studio (SSMS) или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эта процедура позволяет переместить базу данных по новому пути каталога или создать копию базы данных на том же или другом экземпляре сервера.  
    
##  <a name="BeforeYouBegin"></a> Перед началом работы  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При восстановлении базы данных из полной резервной копии системный администратор должен быть единственным пользователем, работающим с базой данных.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Модель восстановления с полным резервным копированием или с неполным протоколированием регламентирует, что перед восстановлением базы данных необходимо создать резервную копию активного журнала транзакций. Дополнительные сведения см. в статье [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)).  

-   Чтобы восстановить зашифрованную базу данных, **требуется доступ к сертификату или асимметричному ключу, использовавшемуся для шифрования этой базы данных.** Без сертификата или асимметричного ключа восстановить базу данных невозможно. Необходимо сохранять сертификат, используемый для шифрования ключа шифрования базы данных, пока существует потребность в резервной копии. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Дополнительные сведения о перемещении базы данных см. в разделе [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md).  
  
-   После восстановления базы данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]база данных автоматически обновляется. Как правило, база данных сразу становится доступной. Но если база данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] содержит полнотекстовые индексы, при обновлении будет произведен их импорт, сброс или повторное создание в зависимости от установленного значения свойства сервера  **upgrade_option** . Если при обновлении выбран режим импорта (**upgrade_option** = 2) или перестроения (**upgrade_option** = 0), полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если для обновления выбран режим «Импортировать», а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены. Чтобы изменить значение свойства сервера **upgrade_option** , следует использовать процедуру [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
###  <a name="Security"></a> безопасность  
 В целях безопасности рекомендуется не присоединять и не восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
####  <a name="Permissions"></a> Permissions  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
  
## <a name="restore-a-database-to-a-new-location-optionally-rename-the-database-using-ssms"></a>Восстановление базы данных в новую папку и при необходимости ее переименование с помощью SSMS 

  
1.  После подключения к соответствующему экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув имя сервера.  
  
2.  Щелкните правой кнопкой мыши элемент **Базы данных**, а затем выберите пункт **Восстановить базу данных**. Откроется диалоговое окно **Восстановление базы данных** .  
  
3.  Чтобы указать источник и расположение восстанавливаемых резервных наборов данных, используйте страницу **Общие** , раздел **Источник** . Выберите один из следующих вариантов.  
  
    -   **База данных**  
  
         Выберите из раскрывающегося списка базу данных для восстановления. Данный список содержит только базы данных, резервное копирование которых было выполнено в соответствии с журналом резервного копирования **msdb** .  
  
    > **ПРИМЕЧАНИЕ.** Если резервная копия была получена с другого сервера, на целевом сервере не будет журнала резервного копирования для указанной базы данных. В этом случае щелкните пункт **Устройство** , чтобы вручную указать файл или устройство для восстановления.  
  
    1.  **Устройство**  
  
         Нажмите кнопку обзора ( **...** ), после чего откроется диалоговое окно **Выбор устройств резервного копирования** . В окне **Тип носителя резервной копии** выберите один из перечисленных типов устройств. Чтобы выбрать одно или несколько устройств в окне **Носитель резервной копии** , нажмите кнопку **Добавить**.  
  
         После добавления нужных устройств в списке **Носитель резервной копии** нажмите кнопку **ОК** для возвращения на страницу **Общие** .  
  
         В списке **Источник: Устройство: База данных** выберите имя базы данных, из которой нужно восстановить резервные копии.  
  
         **Примечание.** Этот список доступен, только если выбрано **Устройство** . Будут выбраны только те базы данных, резервные копии которых доступны на выбранном устройстве.  
  
4.  В разделе **Назначение** , в поле **База данных** автоматически появится имя базы данных для восстановления. Для изменения имени базы данных введите новое имя в окно **База данных** .  
  
5.  В поле **Восстановить до** оставьте значение по умолчанию **До последней выбранной резервной копии** или щелкните **Временную шкалу** , чтобы перейти в диалоговое окно **Временная шкала резервной копии** и выбрать вручную конкретное пороговое время восстановления. Дополнительные сведения об указании конкретного момента времени см. в разделе [Backup Timeline](../../relational-databases/backup-restore/backup-timeline.md) .  
  
6.  В сетке **Резервные наборы данных для восстановления** выберите нужные резервные наборы. В этой сетке отображаются резервные копии, доступные в указанном месте. По умолчанию предлагается план восстановления. Чтобы переопределить предложенный план восстановления, можно изменить выбранные элементы в сетке. Выбор всех резервных копий, которые зависят от восстановления более ранних копий, отменяется автоматически, как только отменяется выбор более ранних копий.  
  
     Дополнительные сведения о столбцах сетки **Восстанавливаемые резервные наборы данных** см. в разделе [Восстановление базы данных (страница "Общие")](../../relational-databases/backup-restore/restore-database-general-page.md).  
  
7.  Чтобы указать новое расположение для файлов баз данных, выберите страницу **Файлы** , а затем нажмите кнопку **Переместить все файлы в папку**. Предоставьте новое расположение для **папки файла данных** и **папки файла журнала**. Дополнительные сведения об этой сетке см. в разделе [Восстановление базы данных (страница "Файлы")](../../relational-databases/backup-restore/restore-database-files-page.md).  
  
8.  На странице **Параметры** настройте параметры, если в этом есть необходимость. Дополнительные сведения об этих параметрах см. в статье [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md).  

 ## <a name="restore-database-to-a-new-location-optionally-rename-the-database-using-t-sql"></a>Восстановление базы данных в новую папку и при необходимости ее переименование с помощью T-SQL
 
 
1.  При необходимости определите логическое и физическое имена файлов в резервном наборе, содержащем полную резервную копию базы данных, которую нужно восстановить. Эта инструкция возвращает список файлов базы данных и журнала, содержащихся в резервном наборе данных. Базовый синтаксис:  
  
     RESTORE FILELISTONLY FROM *<устройство_резервного_копирования>* WITH FILE = *номер_файла_резервного_набора* 
  
     В этом случае аргумент *номер_файла_резервного_набора* указывает позицию резервной копии в наборе носителей. Положение резервного набора можно получить с помощью инструкции [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) . Дополнительные сведения см. в подразделе "Указание резервного набора данных" раздела [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
     Эта инструкция также поддерживает некоторые параметры WITH. Дополнительные сведения см. в разделе [Инструкция RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).  
  
2.  Используйте инструкцию [RESTORE DATABASE](../../t-sql/statements/restore-statements-transact-sql.md) для восстановления полной резервной копии базы данных. По умолчанию файлы данных и журналов восстанавливаются в исходных местоположениях. При перемещении базы данных используйте параметр MOVE, чтобы переместить каждый файл базы данных и избежать конфликтов с существующими файлами.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:  
  
     RESTORE DATABASE *new_database_name*  
  
     FROM *backup_device* [ ,...*n* ]  
  
     [ WITH  
  
     {  
  
     [ **RECOVERY** | NORECOVERY ]  
  
     [ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]  
  
     [ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]  
  
     }  
  
     ;  
  
    > **NOTE!** When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files. This involves using a [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.  
  
     The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location. For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).  
  
     *new_database_name*  
     The new name for the database.  
  
    >**NOTE:** If you are restoring the database to a different server instance, you can use the original database name instead of a new name.  
  
     *backup_device* [ **,**...*n* ]  
     Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored. You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined. To specify a physical backup device, use the DISK or TAPE option:  
  
     { DISK | TAPE } **=**_physical_backup_device_name_  
  
     For more information, see [Backup Devices &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
     { **RECOVERY** | NORECOVERY }  
     If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database. In this case, specify the NORECOVERY option.  
  
     Otherwise, use the RECOVERY option, which is the default.  
  
     FILE = { *backup_set_file_number* | @*backup_set_file_number* }  
     Identifies the backup set to be restored. For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set. You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) statement.  
  
     When this option is not specified, the default is to use the first backup set on the backup device.  
  
     For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
     MOVE **'**_logical_file_name_in_backup_**'** TO **'**_operating_system_file_name_**'** [ **,**...*n* ]  
     Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*. Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |*логическое_имя_файла_в_резервной_копии*|Указывает логическое имя файла данных или журнала в резервном наборе данных. Логическое имя файла данных или журнала в резервном наборе данных соответствует его логическому имени в базе данных на момент создания резервного набора данных.<br /><br /> <br /><br /> Примечание. Для получения списка логических файлов из набора резервных данных следует использовать инструкцию [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).|  
    |*имя_файла_в_операционной_системе*|Задает новое место для файла, указанного параметром *логическое_имя_файла_в_резервной_копии*. Файл будет восстановлен в этом месте.<br /><br /> Параметр *имя_файла_в_операционной_системе* может также указать новое имя для восстановленного файла. Это необходимо, если создается копия существующей базы данных на том же экземпляре сервера.|  
    |*n*|Заполнитель, который показывает, что можно указать дополнительные инструкции MOVE.|  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В приведенном ниже примере создается база данных `MyAdvWorks` посредством восстановления резервной копии образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , в которой содержатся два файла: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data и [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log. В этой базе данных используется простая модель восстановления. База данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] уже существует на экземпляре сервера, поэтому файлы в резервной копии должны быть восстановлены в новом месте. Количество и имена восстанавливаемых файлов базы данных можно определить с помощью инструкции RESTORE FILELISTONLY. Резервная копия базы данных является первым резервным набором данных на устройстве резервного копирования.  
  
> **ПРИМЕЧАНИЕ.** В примерах резервного копирования и восстановления журнала транзакций из резервной копии, включая восстановление на момент времени, используется база данных `MyAdvWorks_FullRM`, которая создается из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], как в следующем примере с базой данных `MyAdvWorks`. Однако полученную базу данных `MyAdvWorks_FullRM` необходимо изменить для использования модели полного восстановления с помощью следующей инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]: ALTER DATABASE <имя_базы_данных> SET RECOVERY FULL.  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 Пример создания полной резервной копии базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] см. в разделе [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Related tasks  
  
-   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Управление метаданными при обеспечении доступности базы данных на другом экземпляре сервера (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)  
  
  
