---
description: sp_ivindexhasnullcols (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fef9d3b131770e11edde117ea12e96d336de24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464222"
---
# <a name="sp_ivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Проверяет уникальность кластеризованного индекса индексированного представления и отсутствие в нем столбцов, которые могут содержать значение NULL в момент, когда индексированное представление должно использоваться для создания публикации транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @viewname = ] 'view_name'` Имя проверяемого представления. Аргумент *view_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @fhasnullcols = ] field_has_null_columns OUTPUT` Флаг, указывающий, содержит ли индекс представления столбцы, допускающие значение NULL. Аргумент *view_name* имеет тип **sysname**и не имеет значения по умолчанию. Возвращает значение **1** , если индекс представления содержит столбцы, ДОПУСКАЮЩИЕ значение null. Возвращает значение **0** , если представление не содержит столбцов, ДОПУСКАЮЩИХ значения NULL.  
  
> [!NOTE]  
>  Если хранимая процедура сама возвращает код возврата **1**, то есть выполнение хранимой процедуры завершилось сбоем, это значение равно **0** , и его следует игнорировать.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_ivindexhasnullcols** используется репликацией транзакций.  
  
 По умолчанию, статьи индексированного представления в публикации создаются как таблицы на подписчиках. Однако если индексированные столбцы допускают значения NULL, индексированное представление создается на подписчике как индексированное представление, а не как таблица. Выполнив данную хранимую процедуру, можно предупредить пользователя о существовании (или отсутствии) данной проблемы в текущем индексированном представлении.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
