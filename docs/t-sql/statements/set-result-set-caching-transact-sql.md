---
title: SET RESULT SET CACHING (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f9750cdc2dea7049bde77d31c275789691abf1b0
ms.sourcegitcommit: 3f2936e727cf8e63f38e5f77b33442993ee99890
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2019
ms.locfileid: "67313816"
---
# <a name="set-result-set-caching-transact-sql"></a>SET RESULT SET CACHING (Transact-SQL) 

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Определяет поведение кэширования результирующего набора для текущего сеанса клиента.  

Область применения этой статьи: хранилище данных SQL Azure (предварительная версия) 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  

**ON**   
Включает кэширование результирующего набора для текущего сеанса клиента.  Для кэширования результирующих наборов невозможно указать значение ON для сеанса, если на уровне базы данных указано значение OFF.

**OFF**   
Отключает кэширование результирующего набора для текущего сеанса клиента.

## <a name="permissions"></a>Разрешения

Требуется членство в роли public.

## <a name="see-also"></a>См. также раздел

[Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)</br>
[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)