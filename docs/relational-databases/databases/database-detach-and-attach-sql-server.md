---
title: "Присоединение и отсоединение базы данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7338e364e970aaccc6c24cdba04e1b43a188c8c9
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="database-detach-and-attach-sql-server"></a>Присоединение и отсоединение базы данных (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Файлы данных и журналов транзакций базы данных можно отсоединить, а затем снова присоединить к тому же или другому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отсоединение и присоединение базы данных полезно, если необходимо переместить базу данных на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на том же компьютере либо перенести базу данных.  
  
  
##  <a name="Security"></a> безопасность  
 Разрешения на доступ к файлам устанавливаются во время выполнения определенных операций с базами данных, включая отсоединение и присоединение баз данных.  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
##  <a name="DetachDb"></a> Отсоединение базы данных  
 Отсоединение базы данных означает удаление ее с экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но сама база данных остается неповрежденной со всеми своими файлами данных и журналов транзакций. Эти файлы затем можно использовать для присоединения базы данных к любому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая сервер, от которого она была отсоединена.  
  
 Базу данных невозможно отсоединить в следующих случаях.  
  
-   База данных реплицируется и публикуется. При репликации база данных должна быть снята с публикации. Перед тем как отсоединить базу данных, необходимо отключить публикацию, выполнив процедуру [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
  
    > [!NOTE]  
    >  Если невозможно использовать процедуру **sp_replicationdboption**, можно удалить репликацию, выполнив процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md).  
  
-   Имеется моментальный снимок базы данных.  
  
     Перед отсоединением базы данных необходимо удалить все моментальные снимки. Дополнительные сведения см. в разделе [Удаление моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md).  
  
    > [!NOTE]  
    >  Невозможно отсоединить или присоединить моментальный снимок базы данных.  
  
-   База данных находится в сеансе зеркального копирования.  
  
     Отключить базу данных невозможно, пока этот сеанс не завершится. Дополнительные сведения см. в разделе [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
-   База данных помечена как подозрительная. Подозрительную базу данных невозможно отсоединить. Для отсоединения ее необходимо перевести в аварийный режим. Дополнительные сведения о переводе базы данных в аварийный режим см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
-   База данных является системной базой данных.  
  
### <a name="backup-and-restore-and-detach"></a>Резервное копирование, восстановление и отсоединение  
 Для разностных резервных копий отсоединение базы данных, доступной только для чтения, приводит к потере сведений о базовой копии для разностного копирования. Дополнительные сведения см. в разделе [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md).  
  
### <a name="responding-to-detach-errors"></a>Реакция на ошибки отсоединения  
 Ошибки, возникшие во время отсоединения базы данных, могут воспрепятствовать чистому закрытию базы данных и перестроению журнала транзакций. При получении сообщения об ошибке выполните следующие действие по исправлению.  
  
1.  Заново присоедините все файлы, связанные с базой данных, а не только первичный файл.  
  
2.  Исправьте неполадку, ставшую причиной сообщения об ошибке.  
  
3.  Отсоедините базу данных повторно.  
  
##  <a name="AttachDb"></a> Присоединение базы данных  
 Можно присоединить скопированную или отсоединенную базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Когда базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с файлами полнотекстовых каталогов присоединяют к экземпляру сервера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , то присоединение файлов каталогов выполняется из их предыдущего расположения вместе с другими файлами баз данных, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в разделе [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md).  
  
 При присоединении базы данных должны быть доступны все файлы данных (файлы MDF и NDF). Если у какого-либо файла данных путь отличается от того, каким он был при первом создании или последнем присоединении, необходимо указать текущий путь к файлу.  
  
> [!NOTE]  
>  Если присоединяемый первичный файл данных доступен только для чтения, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] предполагает, что и база данных доступна только для чтения.  
  
 Когда зашифрованная база данных впервые присоединяется к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ее владелец должен открыть главный ключ базы данных, выполнив следующую инструкцию: OPEN MASTER KEY DECRYPTION BY PASSWORD = **'***пароль***'**. Рекомендуется включить автоматическую расшифровку главного ключа, выполнив следующую инструкцию: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY. Дополнительные сведения см. в разделах [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md) и [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md).  
  
 Требования для присоединения файлов журналов частично зависят от того, доступна база данных для записи и чтения или только для чтения.  
  
-   Для базы данных, доступной для записи и чтения, обычно можно присоединить файл журнала в новом расположении. Однако в некоторых случаях для повторного соединения базы данных требуются файлы ее существующих журналов. Поэтому всегда храните все отсоединенные файлы журналов, пока база данных не будет успешно присоединена без них.  
  
     Если у базы данных, доступной для записи и чтения, только один файл журнала и для него не указано новое расположение, операция присоединения использует старое расположение файла. Если он найден, применяется старый файл журнала независимо от того, была ли база данных выключена чисто. Однако если старый файл журнала не найден и база данных была выключена чисто и не имеет активной цепочки журналов, то операция присоединения пытается построить новый файл журнала для базы данных.  
  
-   Если присоединяемый первичный файл данных доступен только для чтения, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] предполагает, что и база данных доступна только для чтения. Для базы данных, доступной только для чтения, файл или файлы журнала должны быть доступны в расположении, указанном в первичном файле базы данных. Новый файл журнала построить невозможно, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может обновить расположение журнала, указанное в первичном файле.  
  
  
###  <a name="Metadata"></a> Изменение метаданных при присоединении базы данных  
 Если база данных, доступная только для чтения, отсоединяется, а затем снова присоединяется, то данные о текущей базовой копии для разностного копирования будут утеряны. *Базовая копия для разностного копирования* — это последняя из полных резервных копий всех данных из базы данных или из подмножества файлов и файловых групп, содержащихся в базе данных. Без сведений о базовой резервной копии база данных **master** утрачивает синхронизацию с базой данных, доступной только для чтения, и дальнейшее создание разностных резервных копий может привести к непредвиденным результатам. Таким образом, если с базой данных, доступной только для чтения, используются разностные резервные копии, то после повторного присоединения базы данных необходимо установить новую базовую копию для разностного копирования, создав полную резервную копию. Сведения о разностных резервных копиях см. в разделе [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md).  
  
 После присоединения происходит запуск базы данных. Обычно присоединение базы данных переводит ее в то же состояние, в котором она находилась на момент отсоединения или копирования. Однако операции присоединения и отсоединения отключают создание межбазовых цепочек владения для этой базы данных. Сведения о том, как включить цепочки владения, см. в разделе [Параметр конфигурации сервера "cross db ownership chaining"](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md). Также TRUSTWORTHY устанавливается в OFF при каждом присоединении базы данных. Сведения о том, как установить параметр TRUSTWORTHY в значение ON, см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
### <a name="backup-and-restore-and-attach"></a>Резервное копирование, восстановление и присоединение  
 Подобно любой базе данных, которая полностью или частично вне сети, база данных с восстановлением файлов не может быть присоединена. Базу данных можно присоединить после остановки последовательности восстановления. Затем можно снова запустить последовательность восстановления.  
  
###  <a name="OtherServerInstance"></a> Присоединение базы данных к другому экземпляру сервера  
  
> [!IMPORTANT]  
>  База данных, созданная в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не может быть присоединена в ранних версиях.  
  
 При присоединении базы данных к другому экземпляру сервера для обеспечения ее согласованного функционирования для пользователей и приложений может понадобиться повторное создание некоторых или всех метаданных базы данных, например имен входа и задания, на другом экземпляре сервера. Дополнительные сведения см. в статье [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Отсоединение базы данных**  
  
-   [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
-   [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md)  
  
 **Присоединение базы данных**  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
-   [Присоединение базы данных](../../relational-databases/databases/attach-a-database.md)  
  
-   [sp_attach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-db-transact-sql.md)  
  
-   [sp_attach_single_file_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql.md)  
  
 **Обновление базы данных при помощи операций отсоединения и присоединения**  
  
-   [Обновление базы данных при помощи отсоединения и присоединения (Transact-SQL)](../../relational-databases/databases/upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 **Перемещение базы данных при помощи операций отсоединения и присоединения**  
  
-   [Перенос базы данных путем отсоединения и присоединения (язык Transact-SQL)](../../relational-databases/databases/move-a-database-using-detach-and-attach-transact-sql.md)  
  
 **Удаление моментального снимка базы данных**  
  
-   [Удаление моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Файлы и файловые группы базы данных](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
