---
title: Функции работы с наборами строк (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], rowsets
- rowsets [SQL Server], functions
- rowsets [SQL Server]
ms.assetid: ac24d700-3144-4ab5-9fa8-8c014001cc71
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 32997f52602cbcae4d3ed17d0e6e602993a2fcf1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="rowset-functions-transact-sql"></a>Функции наборов строк (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Перечисленные далее функции наборов строк возвращают объект, который можно использовать вместо ссылки на таблицу в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|||  
|-|-|  
|[OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)|[OPENJSON](../../t-sql/functions/openjson-transact-sql.md)|  
|[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)|[OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)|  
|[OPENXML](../../t-sql/functions/openxml-transact-sql.md)||  
  
 Все функции наборов строк являются недетерминированными. Это означает, что данные функции не всегда возвращают одинаковые значения при каждом вызове, даже при одинаковых наборах входных значений. Дополнительные сведения о детерминированности функций см. в статье [Детерминированные и недетерминированные функции](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  
