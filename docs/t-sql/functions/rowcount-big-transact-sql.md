---
title: ROWCOUNT_BIG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f485d550a122ede18b3faea9d1d490a449ab8d54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65942784"
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает число строк, затронутых при выполнении последней инструкции. Эта функция работает подобно [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) за исключением того, что она возвращает значение типа **bigint**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 При использовании после инструкции SELECT данная функция возвращает число строк, возвращенных инструкцией SELECT.  
  
 При использовании после инструкции INSERT UPDATE или DELETE данная функция возвращает число строк, затронутых инструкцией изменения данных.  
  
 При использовании после инструкций, не возвращающих ни одной строки (например, инструкции IF), возвращает 0.  
  
## <a name="see-also"></a>См. также:  
 [COUNT_BIG (Transact-SQL)](../../t-sql/functions/count-big-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
