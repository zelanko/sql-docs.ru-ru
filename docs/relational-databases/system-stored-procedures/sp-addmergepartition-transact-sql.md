---
title: sp_addmergepartition (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 486faeb7d46ee32b40923cd54a018c2005c44621
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760516"
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
 Публикация слиянием, на которой создается секция. *Публикация* — **sysname**, не имеет значения по умолчанию. Если *suser_sname* указан, значение *hostname* должен иметь значение NULL.  
  
 [ **@suser_sname**=] **"***suser_sname***"**  
 Значение, используемое при создании секции для подписки, которая фильтруется по значению [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на стороне подписчика. *SUSER_SNAME* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@host_name**=] **"***host_name***"**  
 Значение, используемое при создании секции для подписки, которая фильтруется по значению [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на стороне подписчика. *HOST_NAME* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepartition** используется в репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergepartition**.  
  
## <a name="see-also"></a>См. также  
 [Создать моментальный снимок для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
