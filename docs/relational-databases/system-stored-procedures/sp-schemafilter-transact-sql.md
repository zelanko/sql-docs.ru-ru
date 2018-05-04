---
title: sp_schemafilter (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1f64ecf275b1a2a8d787de8bf1a51d4520879012
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spschemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет и отображает сведения о схеме, исключенной при построении списка таблиц Oracle, подходящих для публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [**@publisher** =] **"***издатель***"**  
 Имя не[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [**@schema** =] **"***схемы***"**  
 Имя схемы. *схемы* — **sysname**, значение по умолчанию NULL.  
  
 [**@operation** =] **"***операции***"**  
 Действие, выполняемое над этой схемой. *Операция* — **nvarchar(4)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**add**|Добавляет указанную схему в список схем, не подходящих для публикации.|  
|**DROP**|Удаляет указанную схему из списка схем, не подходящих для публикации.|  
|**Справка**|Возвращает список схем, которые не подходят для публикации.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**SchemaName**|**sysname**|Имя схемы, не подходящей для публикации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_schemafilter** следует использовать только для разнородных издателей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе могут выполнять **sp_schemafilter**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
