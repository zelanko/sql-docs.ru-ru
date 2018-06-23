---
title: Псевдонимы столбцов в предложении ORDER BY не могут предваряться псевдонимом таблицы | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 18c65604efb2d1b0ff93d09b8d03f7ee6cb213cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099235"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a>Псевдонимы столбцов в предложении ORDER BY не могут предваряться псевдонимом таблицы
  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях псевдонимы столбцов в предложении ORDER BY не должны предваряться псевдонимами таблицы.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Например, следующий запрос успешно выполняется в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], но в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] завершится ошибкой.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 Компонент [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] не сопоставляет `p.l` в предложении `ORDER BY` допустимому столбцу в таблице.  
  
### <a name="exception"></a>Исключение  
 Если псевдоним таблицы с префиксом, заданный предложением ORDER BY, представляет собой допустимое имя столбца в указанной таблице, то запрос выполняется без ошибки; в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] семантика инструкции может быть иной. Например, псевдоним столбца (`id`), заданный в следующей инструкции, представляет собой допустимое имя столбца в таблице `sysobjects`. При выполнении инструкции в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], операция `CAST` выполняется после сортировки результирующего набора. Это значит, что столбец `name` используется в операции сортировки. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] операция `CAST` выполняется перед операцией сортировки. Это означает, что столбец `id` в таблице используется в операции сортировки и возвращает результирующий набор в непредвиденном порядке.  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените запросы, которые используют псевдонимы столбцов, предваряемые псевдонимами таблиц в предложении ORDER BY, одним из следующих способов.  
  
-   При возможности не указывайте префикс перед псевдонимом столбца в предложении ORDER BY.  
  
-   Замените псевдоним столбца именем столбца.  
  
 Например, оба следующих запроса выполняются без ошибки в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
