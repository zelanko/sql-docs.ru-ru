---
description: NULL и UNKNOWN (Transact-SQL)
title: NULL и UNKNOWN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb30710b35b1e82fafbc50dd7535b99be02ce5ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467563"
---
# <a name="null-and-unknown-transact-sql"></a>NULL и UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL указывает на то, что значение неизвестно. NULL отличается от пустого или нулевого значения. Два значения NULL считаются эквивалентными. Сравнения между двумя значениями NULL или между значением NULL и каким-либо иным значением возвращают неизвестную величину, так как значение каждого из значений NULL неизвестно.  
  
 Значение NULL обычно указывает на то, что данные неизвестны, неприменимы или будут добавлены позже. Например, на момент размещения клиентом заказа может быть неизвестно его отчество.  
  
 Обратите внимание на следующие особенности значений NULL:  
  
-   для проверки наличия значения NULL в предложении WHERE запроса используются ключевые слова IS NULL или IS NOT NULL;  
  
-   значения NULL могут появиться в столбце явным указанием значения NULL в инструкции INSERT или UPDATE или пропуском указания столбца в инструкции INSERT;  
  
-   значения NULL не могут применяться в тех случаях, когда необходимо отличать одну строку таблицы от другой, например в качестве первичного или внешнего ключа, или распределять строки, например в качестве ключа распределения.  
  
 Если в данных присутствуют значения NULL, логические операторы и операторы сравнения могут возвращать, кроме TRUE или FALSE, также и третий результат — UNKNOWN. Эта тройственная логика является источником многих проблем в приложениях. Логические операторы в логическом выражении, включающие значения UNKNOWN, будут возвращать UNKNOWN, за исключением случаев, когда результат оператора не зависит от выражения UNKNOWN. В таблицах содержатся примеры такого поведения.  
  
 В следующей таблице показаны результаты применения оператора AND к двум логическим выражениям, когда одно выражение возвращает UNKNOWN.  
  
|Выражение 1|Выражение 2|Результат|  
|---------------|---------------|------------|  
|true|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 В следующей таблице показаны результаты применения оператора OR к двум логическим выражениям, когда одно выражение возвращает UNKNOWN.  
  
|Выражение 1|Выражение 2|Результат|  
|---------------|---------------|------------|  
|true|UNKNOWN|true|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>См. также  
 [AND (Transact-SQL)](../../t-sql/language-elements/and-transact-sql.md)   
 [OR (Transact-SQL)](../../t-sql/language-elements/or-transact-sql.md)   
 [NOT (Transact-SQL)](../../t-sql/language-elements/not-transact-sql.md)   
 [IS NULL (Transact-SQL)](../../t-sql/queries/is-null-transact-sql.md)  
  
  
