---
title: Методы типа данных XML | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: d112b9c9-be9f-435c-a9e6-d21b65778fb7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 715effa0eb16a298f5064f08d2751df07bfa8677
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020216"
---
# <a name="xml-data-type-methods"></a>Методы типа данных XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Методы типа данных **xml** можно использовать для выполнения запроса к экземпляру XML, хранящемуся в переменной или столбце типа **xml**. Подразделы, входящие в данный раздел, описывают использование методов типа данных **xml**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[query (метод) (тип данных xml)](../../t-sql/xml/query-method-xml-data-type.md)|Описывает, как использовать метод query() для запроса к экземпляру XML.|  
|[value (метод) (тип данных xml)](../../t-sql/xml/value-method-xml-data-type.md)|Описывает, как использовать метод value() для получения значения типа SQL из экземпляра XML.|  
|[exist (метод) (тип данных xml)](../../t-sql/xml/exist-method-xml-data-type.md)|Описывает, как использовать метод exist(), чтобы определить, вернул ли запрос непустой результат.|  
|[modify (метод) (тип данных xml)](../../t-sql/xml/modify-method-xml-data-type.md)|Описывает, как использовать метод modify() и указывать инструкции [языка модификации XML-данных (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md) для выполнения обновлений.|  
|[nodes (метод) (тип данных xml)](../../t-sql/xml/nodes-method-xml-data-type.md)|Описывает, как использовать метод nodes() и разделять XML на несколько строк для распространения XML-документов по наборам строк.|  
|[Привязка реляционных данных внутри данных XML](../../t-sql/xml/binding-relational-data-inside-xml-data.md)|Описывает, как выполнить внутри XML привязку данных, не относящихся к XML.|  
|[Рекомендации по использованию методов для типа данных XML](../../t-sql/xml/guidelines-for-using-xml-data-type-methods.md)|Описывает правила использования методов типа данных **xml**.|  
  
 Эти методы вызываются при помощи синтаксиса вызова метода определяемого пользователем типа. Пример:  
  
```  
SELECT XmlCol.query(' ... ')  
FROM   Table  
```  
  
> [!NOTE]  
>  Методы **query()**, **value()** и **exist()** типа данных **xml** возвращают значение NULL при применении к неопределенному (NULL) экземпляру XML. Кроме того, метод **modify()** ничего не возвращает, а метод **nodes()** возвращает наборы строк и пустой набор строк для входного значения NULL.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров данных XML](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
