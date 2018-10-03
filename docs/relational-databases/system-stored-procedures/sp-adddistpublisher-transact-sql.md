---
title: sp_adddistpublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b8233a5ba3d4610e43dc2c9fb47ba9107ffad268
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716992"
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Настраивает издатель для использования указанной базы данных распространителя. Эта хранимая процедура выполняется на распространителе в любой базе данных. Обратите внимание, что хранимые процедуры [sp_adddistributor &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) и [sp_adddistributiondb &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) должны были быть выполнены перед использованием Эта хранимая процедура.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @storage_connection_string= ] 'storage_connection_string']
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@distribution_db=**] **"***distribution_db***"**  
 Имя базы данных распространителя. *distributor_db* — **sysname**, не имеет значения по умолчанию. Он используется агентами репликации для подключения к издателю.  
  
 [  **@security_mode=**] *security_mode*  
 Реализованный режим обеспечения безопасности. Этот параметр используется только агентами репликации для подключения к издателю обновляемых посредством очередей подписок или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *security_mode* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Агенты репликации на распространителе используют для подключения к издателю проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**1** (по умолчанию)|Агенты репликации на распространителе используют для подключения к издателю проверку подлинности Windows.|  
  
 [  **@login=**] **"***входа***"**  
 Имя входа. Этот параметр является обязательным, если *security_mode* — **0**. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Он используется агентами репликации для подключения к издателю.  
  
 [  **@password=**] **"***пароль***"**]  
 Пароль. *пароль* — **sysname**, значение по умолчанию NULL. Он используется агентами репликации для подключения к издателю.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли.  
  
 [  **@working_directory=**] **"***working_directory***"**  
 Имя рабочего каталога, используемого для хранения файлов данных и схем для публикации. *working_directory* — **nvarchar(255)** и значения по умолчанию папке ReplData текущего для данного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например `C:\Program Files\Microsoft SQL Server\MSSQL\MSSQ.1\ReplData`. Имя должно быть задано в формате UNC.  

 Для базы данных SQL Azure, используйте `\\<storage_account>.file.core.windows.net\<share>`.

 [  **@storage_connection_string =**] **"***storage_connection_string***"**  
 Является обязательным для базы данных SQL. Используйте ключ доступа из портала Azure в группе хранения > Параметры.

 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]

 [  **@trusted=**] **"***доверенных***"**  
 Этот параметр устарел и поддерживается только для обеспечения обратной совместимости. *доверенный* — **nvarchar(5)** и получает только значение **false** приведет к ошибке.  
  
 [  **@encrypted_password=**] *encrypted_password*  
 Установка *encrypted_password* больше не поддерживается. Попытка присвоить этому **бит** параметр **1** приведет к ошибке.  
  
 [  **@thirdparty_flag =**] *thirdparty_flag*  
 Этот аргумент показывает, является ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем. *thirdparty_flag* — **бит**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**1**|База данных, отличная от базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 [ **@publisher_type**=] **"***publisher_type***"**  
 Указывает тип издателя, если издатель не является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* имеет тип sysname и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (по умолчанию).|Используется издатель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Задает стандартного издателя Oracle.|  
|**ORACLE GATEWAY**|Используется издатель Oracle Gateway.|  
  
 Дополнительные сведения о различиях между издателями Oracle и издатель Oracle Gateway см. в разделе [настройка издателя Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_adddistpublisher** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_adddistpublisher**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
