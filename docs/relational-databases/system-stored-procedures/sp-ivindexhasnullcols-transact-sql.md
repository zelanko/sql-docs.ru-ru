---
title: sp_ivindexhasnullcols (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4431ae915c43d6ceb96200c3ebbf6aa976dd4ff3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет уникальность кластеризованного индекса индексированного представления и отсутствие в нем столбцов, которые могут содержать значение NULL в момент, когда индексированное представление должно использоваться для создания публикации транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@viewname**=] **"***view_name***"**  
 Имя представления, для которого требуется проверка. *view_name* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@fhasnullcols**=] *field_has_null_columns* выходных данных  
 Флаг, указывающий, имеются ли в индексе представления столбцы, допускающие значение NULL. *view_name* — **sysname**, не имеет значения по умолчанию. Возвращает значение **1** Если в индексе представления есть столбцы, допускающие значение NULL. Возвращает значение **0** Если представление не содержит столбцов, допускающих значение NULL.  
  
> [!NOTE]  
>  Если сама хранимая процедура возвращает код возврата **1**, то есть выполнение хранимой процедуры завершилось ошибкой, то это значение является **0** и его следует игнорировать.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_ivindexhasnullcols** используется при репликации транзакций.  
  
 По умолчанию, статьи индексированного представления в публикации создаются как таблицы на подписчиках. Однако если индексированные столбцы допускают значения NULL, индексированное представление создается на подписчике как индексированное представление, а не как таблица. Выполнив данную хранимую процедуру, можно предупредить пользователя о существовании (или отсутствии) данной проблемы в текущем индексированном представлении.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
