---
title: "sp_dropdistpublisher (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords: sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8060e5788004b743e58e0d0d424dcc0910459573
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет распространяющего издателя. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=** ] **"***издатель***"**  
 Издатель, которого следует удалить. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@no_checks=** ] *no_checks*  
 Указывает, является ли **sp_dropdistpublisher** проверяет сервер в качестве распространителя издателя. *no_checks* — **бит**, значение по умолчанию **0**.  
  
 Если **0**, репликация проверяет, что удаленный издатель отменил установку локального сервера в качестве распространителя. Если издатель является локальным, репликация проверит отсутствие на локальном сервере объектов публикации или распространителя.  
  
 Если **1**, удаляются все объекты репликации, связанные с распространяющим издателем, даже если удаленный издатель недоступен. После этого удаленный издатель должен удалить репликацию при помощи [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) с  **@ignore_distributor**   =  **1**.  
  
 [  **@ignore_distributor=** ] *ignore_distributor*  
 Указывает, остались ли на распространителе объекты распространения после удаления издателя. *ignore_distributor* — **бит** и может принимать одно из следующих значений:  
  
 **1** = объекты распространения, принадлежащие *издатель* остаются на распространителе.  
  
 **0** = объекты распространения *издатель* очищаются на распространителе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_dropdistpublisher** используется во всех типах репликации.  
  
 При удалении издателя Oracle, если не удалось удалить издатель **sp_dropdistpublisher** возвращает ошибку, а объекты распространителя для издателя удаляются.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_dropdistpublisher**.  
  
## <a name="see-also"></a>См. также:  
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)  (Отключение публикации и распространения)  
 [sp_adddistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
