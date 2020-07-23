---
title: sp_attachsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c039ce9a5f54f3c0498ef613df15353217d91036
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923470"
---
# <a name="sp_attachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]

  Присоединяет существующую базу данных подписки к любому подписчику. Эта хранимая процедура выполняется в базе данных master на новом подписчике.  
  
> [!IMPORTANT]  
>  Данная функция является устаревшей и в следующей версии будет удалена. Использовать эту функцию для новых разработок не рекомендуется. Для публикаций слиянием, секционированных с помощью параметризованных фильтров, рекомендуется использовать новые возможности секционированных снимков, которые упрощают инициализацию большого числа подписок. Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Для несекционированных публикаций можно инициализировать подписку с помощью резервной копии. Дополнительные сведения см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'`Строка, указывающая целевую базу данных подписки по имени. Аргумент *dbname* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @filename = ] 'filename'`— Это имя и физическое расположение основного MDF-**файла (основной** файл данных). *filename* имеет тип **nvarchar (260)** и не имеет значения по умолчанию.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'`Режим безопасности подписчика, используемый при соединении с подписчиком при синхронизации. *subscriber_security_mode* имеет **тип int**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо использовать проверку подлинности Windows. Если *subscriber_security_mode* не равен **1** (проверка подлинности Windows), возвращается ошибка.  
  
`[ @subscriber_login = ] 'subscriber_login'`Имя входа подписчика, используемое при соединении с подписчиком при синхронизации. Аргумент *subscriber_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если *subscriber_security_mode* не равен **1** , а *subscriber_login* указан, возвращается ошибка.  
  
`[ @subscriber_password = ] 'subscriber_password'`Пароль подписчика. Аргумент *subscriber_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Данный аргумент является устаревшим и сохранен только для поддержки обратной совместимости скриптов. Если *subscriber_security_mode* не равен **1** , а *subscriber_password* указан, возвращается ошибка.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Режим безопасности, используемый при соединении с распространителем при синхронизации. *distributor_security_mode* имеет **тип int**и значение по умолчанию **0**. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. **1** указывает проверку подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Имя входа распространителя, используемое при соединении с распространителем при синхронизации. *distributor_login* является обязательным, если *distributor_security_mode* имеет значение **0**. Аргумент *distributor_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Пароль распространителя. *distributor_password* является обязательным, если *distributor_security_mode* имеет значение **0**. Аргумент *distributor_password* имеет тип **sysname**и значение по умолчанию NULL. Значение *distributor_password* должно быть меньше 120 символов Юникода.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый при соединении с издателем при синхронизации. *publisher_security_mode* имеет **тип int**и значение по умолчанию **1**. Если значение **равно 0**, то задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. Если значение равно **1**, указывает проверку подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем при синхронизации. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL. Значение *publisher_password* должно быть меньше 120 символов Юникода.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и не имеет значения по умолчанию. Для соединения агента с распространителем всегда используется эта учетная запись Windows.  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию. Значение *job_password* должно быть меньше 120 символов Юникода.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @db_master_key_password = ] 'db_master_key_password'`Пароль определяемого пользователем главного ключа базы данных. *db_master_key_password* имеет тип **nvarchar (524)** и значение по умолчанию NULL. Если параметр *db_master_key_password* не указан, существующий главный ключ базы данных будет удален и создан повторно.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_attachsubscription** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Подписка не может быть присоединена к публикации, если срок хранения публикации истек. При указании подписки с истекшим сроком хранения публикации возникает ошибка при присоединении или первой синхронизации подписки. Публикации с сроком хранения публикации **0** (никогда не истекает) игнорируются.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_attachsubscription**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
