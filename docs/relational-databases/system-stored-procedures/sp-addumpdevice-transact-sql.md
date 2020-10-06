---
description: sp_addumpdevice (Transact-SQL)
title: sp_addumpdevice (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addumpdevice_TSQL
- sp_addumpdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], defining
- sp_addumpdevice
ms.assetid: c2d2ae49-0808-46d8-8444-db69a69d0ec3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1f17681ffbb922b25cffc6b21ecf2f6317d400db
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753798"
---
# <a name="sp_addumpdevice-transact-sql"></a>sp_addumpdevice (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](../../sql-server/what-s-new-in-sql-server-2016.md)).  

Добавляет в экземпляр компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устройство резервного копирования.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addumpdevice [ @devtype = ] 'device_type'   
    , [ @logicalname = ] 'logical_name'   
    , [ @physicalname = ] 'physical_name'  
      [ , { [ @cntrltype = ] controller_type |  
          [ @devstatus = ] 'device_status' }  
      ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @devtype = ] 'device_type'` — Это тип устройства резервного копирования. *device_type* имеет тип **varchar (20)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**свободного**|Файл на жестком диске в качестве устройства резервного копирования.|  
|**аудиокассет**|Любое ленточное устройство, поддерживаемое [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.<br /><br /> Примечание. Поддержка ленточных устройств резервного копирования будет удалена в одной из будущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.|  
  
`[ @logicalname = ] 'logical_name'` Логическое имя устройства резервного копирования, используемое в инструкциях BACKUP и RESTORE. Аргумент *logical_name* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @physicalname = ] 'physical_name'` Физическое имя устройства резервного копирования. Физические имена должны соответствовать правилам для имен файлов операционной системы или формату UNC для сетевых устройств и должны содержать полный путь. *physical_name* имеет тип **nvarchar (260)**, не имеет значения по умолчанию и не может иметь значение null.  
  
 При создании устройства резервного копирования в удаленном сетевом каталоге убедитесь, что имя входа, под которым запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], имеет на удаленном компьютере необходимые права на запись.  
  
 При добавлении ленточного устройства этот параметр должен быть физическим именем, назначенным локальному ленточному устройству системой Windows. Например, ** \\ \\ .\TAPE0** для первого ленточного устройства на компьютере. Ленточное устройство должно быть подключено к серверному компьютеру и его нельзя использовать удаленно. Имена команд, содержащие символы, отличные от алфавитно-цифровых, следует заключать в кавычки.  
  
> [!NOTE]  
>  Эта процедура вносит указанное физическое имя в каталог. Она не пытается создать это устройство или произвести доступ к нему.  
  
`[ @cntrltype = ] 'controller_type'` Устаревшие. Если указан — не обрабатывается. Поддерживается исключительно в целях обратной совместимости. Новые варианты использования **sp_addumpdevice** должны опускать этот параметр.  
  
`[ @devstatus = ] 'device_status'` Устаревшие. Если указан — не обрабатывается. Поддерживается исключительно в целях обратной совместимости. Новые варианты использования **sp_addumpdevice** должны опускать этот параметр.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_addumpdevice** добавляет устройство резервного копирования в представление каталога **sys.backup_devices** . После этого устройство можно указывать в инструкциях BACKUP и RESTORE по логическому имени. **sp_addumpdevice** не выполняет никакого доступа к физическому устройству. Обращение к нему производится только при выполнении инструкций BACKUP и RESTORE. Создание логического устройства резервного копирования упрощает инструкции BACKUP и RESTORE, позволяя вместо пути устройства в предложениях TAPE = и DISK = указывать имена устройств.  
  
 При использовании дисковых и файловых устройств резервного копирования проблемы владения и разрешений могут накладываться. Проверьте, даны ли необходимые разрешения на соответствующие файлы учетной записи Windows, от имени которой запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] поддерживает резервное копирование на ленточные устройства, которые поддерживаются Windows. Дополнительные сведения о ленточных устройствах, поддерживаемых Windows, см. в списке оборудования, совместимого с Windows. Для просмотра списка ленточных устройств, доступных на компьютере, воспользуйтесь средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Пользуйтесь только теми типами лент, которые рекомендованы производителем устройства. Для накопителей на цифровых звуковых лентах (DAT) пользуйтесь лентами компьютерного класса (хранилище цифровых данных — DDS).  
  
 **sp_addumpdevice** не может выполняться внутри транзакции.  
  
 Чтобы удалить устройство, используйте [sp_dropdevice](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md) или[SQL Server Management Studio](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
 Необходимо разрешение на запись на жесткий диск.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-disk-dump-device"></a>A. Добавление дискового устройства хранения  
 В следующем примере добавляется дисковое устройство резервного копирования с именем `mydiskdump`, которое имеет физическое имя `c:\dump\dump1.bak`.  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak';  
```  
  
### <a name="b-adding-a-network-disk-backup-device"></a>Б. Добавление сетевого дискового устройства резервного копирования  
 Следующий пример иллюстрирует добавление удаленного дискового устройства резервного копирования с именем `networkdevice`. Имя, от которого запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], должно иметь разрешения на удаленный файл (`\\<servername>\<sharename>\<path>\<filename>.bak`).  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'networkdevice',  
    '\\<servername>\<sharename>\<path>\<filename>.bak';  
```  
  
### <a name="c-adding-a-tape-backup-device"></a>В. Добавление ленточного устройства резервного копирования  
 В следующем примере добавляется устройство `tapedump1` с физическим именем `\\.\tape0`.  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0';  
```  
  
### <a name="d-backing-up-to-a-logical-backup-device"></a>Г. Резервное копирование на логическое устройство резервного копирования  
 В следующем примере создается логическое устройство резервного копирования `AdvWorksData` для файла резервной копии на диске. Затем показано, как производится резервное копирование базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на это логическое устройство резервного копирования.  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksData',   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\BACKUP\AdvWorksData.bak';  
GO  
BACKUP DATABASE AdventureWorks2012   
 TO AdvWorksData  
   WITH FORMAT;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [sp_dropdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [sys.backup_devices (Transact-SQL)](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
