---
title: "Методы типа данных XML | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: d112b9c9-be9f-435c-a9e6-d21b65778fb7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fcf16bd9b71f27ab91fb02bbfd7bb7625185b44e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-type-methods"></a>Методы типа данных XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Можно использовать **xml** методы для запроса к экземпляру XML, хранимых в переменной или столбце типа данных **xml** типа. В подразделах этого раздела описывается использование **xml** методов типа данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[запрос &#40; &#41; Метод &#40; тип данных xml &#41;](../../t-sql/xml/query-method-xml-data-type.md)|Описывает, как использовать метод query() для запроса к экземпляру XML.|  
|[значение &#40; &#41; Метод &#40; тип данных xml &#41;](../../t-sql/xml/value-method-xml-data-type.md)|Описывает, как использовать метод value() для получения значения типа SQL из экземпляра XML.|  
|[существует &#40; &#41; Метод &#40; тип данных xml &#41;](../../t-sql/xml/exist-method-xml-data-type.md)|Описывает, как использовать метод exist(), чтобы определить, вернул ли запрос непустой результат.|  
|[Изменить &#40; &#41; Метод &#40; тип данных xml &#41;](../../t-sql/xml/modify-method-xml-data-type.md)|Описывает, как использовать метод modify() для указания [языка XML DML &#40; Язык XML DML &#41; ](../../t-sql/xml/xml-data-modification-language-xml-dml.md)инструкции для выполнения обновлений.|  
|[узлы &#40; &#41; Метод &#40; тип данных xml &#41;](../../t-sql/xml/nodes-method-xml-data-type.md)|Описывает, как использовать метод nodes() и разделять XML на несколько строк для распространения XML-документов по наборам строк.|  
|[Привязка реляционных данных внутри данных XML](../../t-sql/xml/binding-relational-data-inside-xml-data.md)|Описывает, как выполнить внутри XML привязку данных, не относящихся к XML.|  
|[Рекомендации по использованию методов для типа данных XML](../../t-sql/xml/guidelines-for-using-xml-data-type-methods.md)|Описывает рекомендации по использованию **xml** методов типа данных.|  
  
 Эти методы вызываются при помощи синтаксиса вызова метода определяемого пользователем типа. Например:  
  
```  
SELECT XmlCol.query(' ... ')  
FROM   Table  
```  
  
> [!NOTE]  
>  **Xml** методов типа данных **query()**, **value()**, и **exist()** вернуть значение NULL, если выполняемые в экземпляр NULL XML. Кроме того **modify()** ничего не возвращает, но **nodes()** Возвращает наборы строк и пустой набор строк входного значения NULL.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров данных XML](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  

