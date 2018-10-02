---
title: Использование предложения FOR XML для создания XML на основе набора строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b1555b97b1d6f31c8d7aef6b002e1c9f05c976be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856512"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a>Использование предложения XML FOR для создания XML на основе набора строк
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  На основе набора строк можно создать экземпляр типа данных **xml** , используя инструкцию FOR XML с новой директивой **TYPE** .  
  
 Результат может быть назначен столбцу, переменной или параметру типа **xml** . Кроме того, инструкции FOR XML могут быть вложены друг в друга, создавая произвольные иерархические структуры. Благодаря этому создавать вложенные инструкции FOR XML намного проще, чем FOR XML EXPLICIT, но при большой глубине иерархии они могут оказаться менее эффективными. Предложение FOR XML поддерживает также новый режим PATH. Этот режим определяет в дереве XML путь к значению столбца.  
  
 Новая директива **FOR XML TYPE** позволяет определять для реляционных данных XML-представления, поддерживающие только чтение, используя синтаксис SQL. Как показано в следующих примерах, представление можно запрашивать при помощи инструкций SQL и встроенного механизма XQuery. К этим SQL-представлениям можно также обращаться в хранимых процедурах.  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a>Пример. SQL-представление, возвращающее сформированный тип данных XML  
 Следующий код создает XML-представление для реляционного столбца pk и заносит в него информацию об авторах, извлекаемую из XML-столбца:  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 Представление V содержит единственную строку с единственным столбцом xmlVal XML-типа`.` . Его можно запрашивать так же, как и обычный экземпляр типа данных **xml** . Например, следующий запрос возвращает сведения об авторе по имени «David»:  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 Определения SQL-представлений в чем-то похожи на XML-представления, создаваемые с использованием аннотированных схем. Однако между ними есть важные различия. Определение SQL-представления поддерживает только чтение, а работать с ним нужно, используя встроенный механизм XQuery. XML-представления создаются при помощи аннотированной схемы. Кроме того, SQL-представление материализует XML-результаты перед применением выражения XQuery, тогда как при запросах XPath для XML-представлений выполняются SQL-запросы базовых таблиц.  
  
## <a name="see-also"></a>См. также:  
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
