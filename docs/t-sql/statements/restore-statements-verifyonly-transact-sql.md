---
title: "RESTORE VERIFYONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VERIFYONLY
- RESTORE VERIFYONLY
- VERIFYONLY_TSQL
- RESTORE_VERIFYONLY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- RESTORE VERIFYONLY statement
- backups [SQL Server], verifying
- verifying backups
- checking backups
ms.assetid: cba3b6a0-b48e-4c94-812b-5b3cbb408bd6
caps.latest.revision: "64"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b5cd93baf9fc13bd5333f5589dbb56413091671a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---verifyonly-transact-sql"></a>Инструкции - RESTORE VERIFYONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет, но не восстанавливает резервную копию, а также проверяет полноту резервного набора данных и возможность его считывания. Однако инструкция RESTORE VERIFYONLY не проверяет структуру данных, содержащихся в томах резервной копии. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], инструкция RESTORE VERIFYONLY была расширена для проведения дополнительной проверки данных для увеличения вероятности обнаружения ошибок. Цель — приблизиться к настоящей операции восстановления, насколько это возможно. Дополнительные сведения см. в разделе «Примечания».  
  
 Если резервная копия действительна, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает сообщение об успешном выполнении.  
  
> [!NOTE]  
>  Описания аргументов см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE VERIFYONLY  
FROM <backup_device> [ ,...n ]  
[ WITH    
 {  
   LOADHISTORY   
  
--Restore Operation Option  
 | MOVE 'logical_file_name_in_backup' TO 'operating_system_file_name'   
          [ ,...n ]   
  
--Backup Set Options  
 | FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Monitoring Options  
 | STATS [ = percentage ]   
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 Описания аргументов инструкции RESTORE VERIFYONLY см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 Набор носителей или резервный набор данных должен содержать минимально верные данные, чтобы интерпретироваться как формат Microsoft Tape Format. В противном случае инструкция RESTORE VERIFYONLY прекращает выполнение и показывает, что формат резервной копии недопустим.  
  
 Проверки, выполняемые инструкцией RESTORE VERIFYONLY, включают:  
  
-   Проверку полноты резервного набора данных и доступности для чтения всех томов.  
  
-   Некоторые поля заголовков страниц базы данных, например идентификатор страницы (как если бы инструкция записывала данные).  
  
-   Контрольную сумму (если она имеется на носителе).  
  
-   Проверку свободного места на целевых устройствах.  
  
> [!NOTE]  
>  Инструкция RESTORE VERIFYONLY не применяется в отношении моментальных снимков базы данных. Проверка моментального снимка базы данных перед операцией восстановления до предыдущего состояния выполняется с помощью инструкции DBCC CHECKDB.  
  
> [!NOTE]  
>  Резервные копии моментальных снимков RESTORE VERIFYONLY подтверждает наличие моментальных снимков в местоположении, указанном в файле резервной копии. Резервные копии моментальных снимков — это новая функция в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Дополнительные сведения о резервных копий моментальных снимков см. в разделе [резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
## <a name="security"></a>безопасность  
 В операции создания резервной копии могут дополнительно указываться пароли для набора носителей, резервного набора данных или и того и другого. Если для набора носителей или резервного набора данных установлен пароль, то в инструкции RESTORE необходимо указывать правильные пароли. Эти пароли предотвращают несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи инструментальных средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Защита резервных копий, рекомендуется хранить ленты резервной копии в безопасном месте или создать резервную копию файлов, которые защищены списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Разрешения  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях, чтобы получить сведения о резервном наборе данных или устройстве резервного копирования, необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
