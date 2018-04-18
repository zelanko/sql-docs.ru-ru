---
title: sp_addmergepartition (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a169b85f0ae207f72ba0f142633aa323403745c3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spaddmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает динамически фильтруемую секцию для подписки, которая фильтруется по значениям [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) или [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. Данная хранимая процедура выполняется на издателе публикуемой базы данных и используется для создания секций вручную.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Публикация слиянием, на которой создается секция. *Публикация* — **sysname**, не имеет значения по умолчанию. Если *suser_sname* указано, значение *hostname* должен иметь значение NULL.  
  
 [ **@suser_sname**=] **"***suser_sname***"**  
 Значение, используемое при создании секции для подписки, которая фильтруется по значению [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на стороне подписчика. *функция SUSER_SNAME* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@host_name**=] **"***host_name***"**  
 Значение, используемое при создании секции для подписки, которая фильтруется по значению [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на стороне подписчика. *HOST_NAME* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addmergepartition** используется в репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addmergepartition**.  
  
## <a name="see-also"></a>См. также  
 [Создать моментальный снимок для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
