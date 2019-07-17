---
title: sp_ivindexhasnullcols (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27ebcdf656effb97529bea42972be96f9a993cfc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139906"
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
`[ @viewname = ] 'view_name'` — Имя представления для проверки. *view_name* — **sysname**, не имеет значения по умолчанию.  
  
`[ @fhasnullcols = ] field_has_null_columns OUTPUT` Флаг, указывающий, имеются ли в индексе представления столбцы, допускающие значение NULL. *view_name* — **sysname**, не имеет значения по умолчанию. Возвращает значение **1** Если в индексе представления есть столбцы, допускающие значение NULL. Возвращает значение **0** Если представление не содержит столбцов, допускающих значения NULL.  
  
> [!NOTE]  
>  Если сама хранимая процедура возвращает код возврата **1**, то есть выполнение хранимой процедуры завершилось ошибкой, то это значение равно **0** и его следует игнорировать.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_ivindexhasnullcols** используется репликацией транзакций.  
  
 По умолчанию, статьи индексированного представления в публикации создаются как таблицы на подписчиках. Однако если индексированные столбцы допускают значения NULL, индексированное представление создается на подписчике как индексированное представление, а не как таблица. Выполнив данную хранимую процедуру, можно предупредить пользователя о существовании (или отсутствии) данной проблемы в текущем индексированном представлении.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
