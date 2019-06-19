---
title: Логические операторы (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], logical
- testing truth
- truth testing
- "TRUE"
- "FALSE"
- logical operators [SQL Server], Transact-SQL
ms.assetid: edd92f08-76fb-4fd7-a4b6-8520d6a81df1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fb17d3747f7b8e59994e20ec660f3ac7a60bbbc6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982038"
---
# <a name="logical-operators-transact-sql"></a>Логические операторы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Логические операторы проверяют истину некоторого условия. Логические операторы, например оператор сравнения, возвращают тип данных **Boolean** со значениями TRUE, FALSE или UNKNOWN.  
  
|Оператор|Значение|  
|--------------|-------------|  
|[ALL](../../t-sql/language-elements/all-transact-sql.md)|TRUE, если все сравнения в наборе равны TRUE.|  
|[AND](../../t-sql/language-elements/and-transact-sql.md)|TRUE, если оба выражения типа Boolean равны TRUE.|  
|[ANY](../../t-sql/language-elements/any-transact-sql.md)|TRUE, если любое из сравнений в наборе равно TRUE.|  
|[BETWEEN](../../t-sql/language-elements/between-transact-sql.md)|TRUE, если операнд принадлежит указанному диапазону.|  
|[EXISTS](../../t-sql/language-elements/exists-transact-sql.md)|TRUE, если вложенный запрос возвращает как минимум одну строку.|  
|[IN](../../t-sql/language-elements/in-transact-sql.md)|TRUE, если операнд содержится в заданном списке выражений.|  
|[LIKE](../../t-sql/language-elements/like-transact-sql.md)|TRUE, если оператор удовлетворяет шаблону.|  
|[NOT](../../t-sql/language-elements/not-transact-sql.md)|Меняет значение оператора типа Boolean на противоположное.|  
|[OR](../../t-sql/language-elements/or-transact-sql.md)|TRUE, если одно из выражений типа Boolean равно TRUE.|  
|[SOME](../../t-sql/language-elements/some-any-transact-sql.md)|TRUE, если некоторые из сравнений в наборе равны TRUE.|  
  
## <a name="see-also"></a>См. также:  
 [Приоритет операторов (Transact-SQL)](../../t-sql/language-elements/operator-precedence-transact-sql.md)  
  
  
