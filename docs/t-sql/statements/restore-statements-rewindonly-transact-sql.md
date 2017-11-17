---
title: "RESTORE REWINDONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs:
- TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 731cb91434fcf193d7a3391151400942061dfd21
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---rewindonly-transact-sql"></a>Инструкции - RESTORE REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перематывает на начало и закрывает указанное ленточное устройство, если оно осталось открытым после выполнения инструкции BACKUP или RESTORE без аргумента NOREWIND. Эта команда поддерживается только для ленточных устройств.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>Аргументы  
 **\<устройство_резервного_копирования >:: =** 
  
 Логическое или физическое устройство резервного копирования.  
  
 { *logical_backup_device_name* | **@***logical_backup_device_name_var* }  
 Логическое имя должно соответствовать правилам для идентификаторов устройств резервного копирования, созданные **sp_addumpdevice** из которого восстанавливается база данных. Если указано как переменная (**@***logical_backup_device_name_var*), имя устройства резервного копирования может быть задано в виде строковой константы ( **@**  *logical_backup_device_name_var* = *logical_backup_device_name*) или как переменную строкового типа данных, за исключением **ntext** или **текст** типов данных.  
  
 {ДИСК | ЛЕНТА}  **=**  { **"***имя_физического_устройства_резервного _копирования***"**  |   **@**  *переменная_имени_физического_устройства_резервного _копирования* }  
 Разрешает сохранение резервных копий с названного диска или ленточного устройства хранения данных. Типы дисковых и магнитных устройств должны быть заданы с фактическое имя (например, полный путь и имя файла) устройства: ДИСК = 'C:\Program Files\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' или TAPE = '\\\\. \TAPE0 ". Если указано как переменная (**@***переменная_имени_физического_устройства_резервного _копирования*), имя устройства может быть задано в виде строковой константы ( **@**  *переменная_имени_физического_устройства_резервного _копирования* = "*physcial_backup_device_name*") или как переменную строкового типа данных, за исключением **ntext**или **текст** типов данных.  
  
 Укажите тип дискового устройства с помощью сетевого сервера с именем UNC (которое должно содержать имя компьютера). Дополнительные сведения об использовании имен UNC см. в разделе [устройства резервного копирования &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Учетная запись, под которой выполняется Microsoft SQL Server должен иметь доступ на чтение к удаленному компьютеру или серверу сети для выполнения операции восстановления.  
  
 *n*  
 Заполнитель, указывающий на наличие нескольких устройств резервного копирования, а также на возможность задать логическое устройство резервного копирования. Максимальное число устройств резервного копирования или логических устройств резервного копирования является **64**.  
  
 Необходимость наличия при восстановлении того же количества устройств резервного копирования, какое было использовано для создания набора носителей (которым принадлежат резервные копии), зависит от режима восстановления. Восстановление в сети позволяет использовать меньше устройств, чем было задействовано при создании резервных копий. При восстановлении в сети обязательно наличие всех устройств резервного копирования. Попытка выполнить восстановление с меньшим числом устройств не будет успешно завершена.  
  
 Дополнительные сведения см. в разделе [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
> [!NOTE]  
>  Восстанавливая резервные копии с зеркального набора носителей, можно указать по одному зеркалу для каждого семейства носителей. Но в случае возникновения ошибок наличие других зеркал способствует быстрому устранению некоторых неполадок при восстановлении. Поврежденный том носителя можно заменить соответствующим томом с другого зеркала. Обратите внимание, что для восстановления вне сети можно использовать меньше устройств, чем семейств носителей, однако каждое семейство обрабатывается только один раз.  
  
 **С параметрами**  
  
 UNLOAD  
 Означает автоматическую перемотку и выгрузку ленты по завершении инструкции RESTORE. При запуске нового сеанса пользователя выполнение параметра UNLOAD задано по умолчанию. Оно остается заданным до тех пор, пока не будет задан параметр NOUNLOAD. Этот параметр применяется только с ленточными устройствами. Если при выполнении инструкции RESTORE используется другой тип устройств резервного копирования, то этот параметр не учитывается.  
  
 NOUNLOAD  
 Указывает, что по выполнении инструкции RESTORE лента из ленточного устройства автоматически не выгружается. NOUNLOAD остается установленным до тех пор, пока указано UNLOAD.  
  
 Указывает, что по выполнении инструкции RESTORE лента из ленточного устройства автоматически не выгружается. NOUNLOAD остается установленным до тех пор, пока указано UNLOAD.  
  
## <a name="general-remarks"></a>Общие замечания  
 RESTORE REWINDONLY является альтернативой RESTORE LABELONLY FROM TAPE = \<имя > WITH REWIND. Можно получить список открытых ленточных устройств [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) динамическое административное представление.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Инструкцию RESTORE REWINDONLY может выполнять любой пользователь.  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  


