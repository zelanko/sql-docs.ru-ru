---
title: sp_validate_replica_hosts_as_publishers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_validate_replica_hosts_as_publishers_TSQL
- sp_validate_replica_hosts_as_publishers
helpviewer_keywords:
- sp_validate_replica_hosts_as_publishers
ms.assetid: 45001fc9-2dbd-463c-af1d-aa8982d8c813
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9143c5c681ed9e992a06ccad6be4511c23be37b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639699"
---
# <a name="spvalidatereplicahostsaspublishers-transact-sql"></a>sp_validate_replica_hosts_as_publishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **sp_validate_replica_hosts_as_publishers** является расширением **sp_validate_redirected_publisher** , позволяющий все вторичные реплики для проверки, а не только текущей первичной реплики. **sp_validate_replicat_hosts_as_publisher** проверяет всю Always On репликации топологию. **sp_validate_replica_hosts_as_publishers** должна выполняться прямо для распространителя с помощью сеанса удаленного рабочего стола, чтобы избежать ошибки безопасности двойного прыжка (21892).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_validate_replica_hosts_as_publishers   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@original_publisher** =] **"***original_publisher***"**  
 Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], первоначально опубликовавшего базу данных. *original_publisher* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@publisher_db** =] **"***publisher_db***"**  
 Имя опубликованной базы данных. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@redirected_publisher** =] **"***redirected_publisher***"**  
 Цель перенаправления при **sp_redirect_publisher** был вызван для первоначальный издатель/опубликованная база данных пары. *redirected_publisher* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Если не существует запись для издателя и базы данных публикации, **sp_validate_redirected_publisher** возвращает значение null, если для параметра вывода *@redirected_publisher*. В противном случае происходит возврат связанного перенаправленного издателя как в случае успеха, так и в случае неудачи.  
  
 Если проверка прошла успешно, **sp_validate_redirected_publisher** Возвращает указание на успех.  
  
 Если проверка завершается неудачно, формируются соответствующие ошибки.  **sp_validate_redirected_publisher** делает обнаружил максимум усилий для вызова обо всех проблемах и не только первый.  
  
> [!NOTE]  
>  Работа**sp_validate_replica_hosts_as_publishers** завершится сбоем со следующей ошибкой при проверке узлов вторичной реплики, которые не допускают доступ для чтения либо требуют указания намерения чтения.  
>   
>  Сообщение 21899, уровень 11, состояние 1, процедура **sp_hadr_verify_subscribers_at_publisher**, строка 109  
>   
>  Запрос на перенаправленном издателе «MyReplicaHostName» для определения того, имеются ли записи sysserver для подписчиков исходного издателя «MyOriginalPublisher» , завершился с ошибкой «976»; сообщение об ошибке: «Ошибка 976, уровень 14, состояние 1, сообщение: Целевая база данных «MyPublishedDB» участвует в группе доступности и в настоящее время недоступна для запросов. Либо перемещение данных приостанавливается, либо реплика доступности не разрешена для чтения. Чтобы разрешить доступ только для чтения к этой и другим базам данных в группе доступности, задайте доступ для чтения одной или нескольким вторичным репликам доступности в группе.  Дополнительные сведения см. в описании инструкции **ALTER AVAILABILITY GROUP** в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
>   
>  Произошла одна или несколько ошибок проверки издателя для узла реплики «MyReplicaHostName».  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть либо членом **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных для базы данных распространителя или членом списка доступа публикации для определенной публикации связанные с базой данных издателя.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)  
  
  
