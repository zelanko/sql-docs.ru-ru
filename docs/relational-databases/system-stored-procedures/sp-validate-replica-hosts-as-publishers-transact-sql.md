---
title: sp_validate_replica_hosts_as_publishers (T-SQL)
description: Описывает sp_validate_replica_hosts_as_publishers хранимую процедуру, которая позволяет проверять все вторичные реплики.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validate_replica_hosts_as_publishers_TSQL
- sp_validate_replica_hosts_as_publishers
helpviewer_keywords:
- sp_validate_replica_hosts_as_publishers
ms.assetid: 45001fc9-2dbd-463c-af1d-aa8982d8c813
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9375be2a2af2b7653b3f0f036405533f1571ff3f
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75320013"
---
# <a name="sp_validate_replica_hosts_as_publishers-transact-sql"></a>sp_validate_replica_hosts_as_publishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **sp_validate_replica_hosts_as_publishers** является расширением **sp_validate_redirected_publisher** , позволяющим проверять все вторичные реплики, а не только текущую первичную реплику. **sp_validate_replicat_hosts_as_publisher** проверяет всю топологию репликации Always on. **sp_validate_replica_hosts_as_publishers** должны выполняться непосредственно на распространителе с помощью сеанса удаленного рабочего стола, чтобы избежать ошибки безопасности двойного прыжка (21892).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [соглашения о синтаксисе Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_validate_replica_hosts_as_publishers   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @original_publisher = ] 'original_publisher'`Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который первоначально опубликовал базу данных. Аргумент *original_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя публикуемой базы данных. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @redirected_publisher = ] 'redirected_publisher'`Целевой объект перенаправления при вызове **sp_redirect_publisher** для исходной пары издателей и опубликованных баз данных. Аргумент *redirected_publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 Если для издателя и базы данных публикации не существует записи, **sp_validate_redirected_publisher** возвращает значение NULL для выходного параметра * \@redirected_publisher*. В противном случае происходит возврат связанного перенаправленного издателя как в случае успеха, так и в случае неудачи.  
  
 Если проверка завершается успешно, **sp_validate_redirected_publisher** Возвращает индикатор успеха.  
  
 Если проверка завершается неудачно, формируются соответствующие ошибки.  **sp_validate_redirected_publisher** наилучшим образом выдать все проблемы, а не только первый.  
  
> [!NOTE]  
>  **sp_validate_replica_hosts_as_publishers** завершится со следующей ошибкой при проверке узлов вторичной реплики, которые не разрешают доступ на чтение, или если требуется указать намерение Read.  
>   
>  Сообщение 21899, уровень 11, состояние 1, процедура **sp_hadr_verify_subscribers_at_publisher**, строка 109  
>   
>  Запрос на перенаправленном издателе «MyReplicaHostName» для определения того, имеются ли записи sysserver для подписчиков исходного издателя «MyOriginalPublisher» , завершился с ошибкой «976»; сообщение об ошибке: «Ошибка 976, уровень 14, состояние 1, сообщение: Целевая база данных «MyPublishedDB» участвует в группе доступности и в настоящее время недоступна для запросов. Либо перемещение данных приостанавливается, либо реплика доступности не разрешена для чтения. Чтобы разрешить доступ только для чтения к этой и другим базам данных в группе доступности, задайте доступ для чтения одной или нескольким вторичным репликам доступности в группе.  Дополнительные сведения см. в описании инструкции **ALTER AVAILABILITY GROUP** в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
>   
>  Произошла одна или несколько ошибок проверки издателя для узла реплики «MyReplicaHostName».  
  
## <a name="permissions"></a>Разрешения  
 Участник должен быть членом предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа к публикации для определенной публикации, связанной с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)  
  
  
