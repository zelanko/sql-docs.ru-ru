---
title: "Значение NULL и UNKNOWN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d0523877d572bd644fa772713f3c7edb82d645f2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="null-and-unknown-transact-sql"></a>Значение NULL и UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL означает, что значение неизвестно. Значение null отличается от пустого или нулевого значения. Два значения NULL считаются эквивалентными. Сравнения между двумя значениями null или между значением null и любое другое значение, возвращают неизвестную, так как значение каждого из значений NULL неизвестно.  
  
 Значение NULL обычно указывает данные, которые неизвестны, неприменимы, или которая будет добавлена позже. Например, на момент размещения клиентом заказа может быть неизвестно его отчество.  
  
 Обратите внимание на следующие особенности значения null.  
  
-   для проверки наличия значения NULL в предложении WHERE запроса используются ключевые слова IS NULL или IS NOT NULL;  
  
-   Значения NULL могут вставляться в столбце явным указанием значения NULL в инструкции INSERT или UPDATE, или пропуском указания столбца в инструкции INSERT.  
  
-   Значения NULL не может использоваться как сведения, когда необходимо отличать одну строку таблицы от другой таблицы, например первичные ключи или сведения, используемые для распространения строк, например распространения ключей.  
  
 Если в данных присутствуют значения NULL, логические операторы и операторы сравнения могут возвращать, кроме TRUE или FALSE, также и третий результат — UNKNOWN. Эта тройственная логика является источником многих проблем в приложениях. Приведенные ниже таблицы показывают, как значения NULL влияют на операции сравнения.  
  
 Ниже приведены результаты применения оператора AND к двум логическим операндам где один операнд возвращает значение NULL.  
  
|Операнд 1|Операндом 2|Результат|  
|---------------|---------------|------------|  
|TRUE|NULL|FALSE|  
|NULL|NULL|FALSE|  
|FALSE|NULL|FALSE|  
  
 Ниже приведены результаты применения оператора OR к двум логическим операндам где один операнд возвращает значение NULL.  
  
|Операнд 1|Операндом 2|Результат|  
|---------------|---------------|------------|  
|TRUE|NULL|TRUE|  
|NULL|NULL|UNKNOWN|  
|FALSE|NULL|UNKNOWN|  
  
## <a name="see-also"></a>См. также:  
 [И &#40; Transact-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [ИЛИ &#40; Transact-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [НЕ &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [РАВЕН NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
