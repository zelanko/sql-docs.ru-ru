---
title: "XML (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e85eb245cf9d53f7d38579928a5145828797002
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Тип данных, в котором хранятся XML-данные. Можно хранить **xml** экземпляров в столбце или переменной **xml** типа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Аргументы  
 CONTENT  
 Ограничивает **xml** экземпляр должен иметь правильный формат XML-фрагмент. XML-данные могут содержать несколько (0 или больше) элементов верхнего уровня. Текстовые узлы разрешены на верхнем уровне.  
  
 Это поведение по умолчанию.  
  
 DOCUMENT  
 Ограничивает **xml** экземпляр должен иметь правильный формат XML-документа. XML-данные должны содержать только один корневой элемент. Текстовые узлы на верхнем уровне запрещены.  
  
 *xml_schema_collection*  
 Имя коллекции XML-схем. Чтобы создать типизированный **xml** столбца или переменной, при необходимости можно указать имя коллекции схем XML. Дополнительные сведения о типизированном и нетипизированном XML, см. в разделе [сравнение типизированного XML нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Замечания  
 Размер хранимого представления **xml** экземпляры типа данных не может превышать 2 гигабайт (ГБ).  
  
 Аспекты CONTENT и DOCUMENT применяются только к типизованным XML. Дополнительные сведения см. [сравнение типизированного XML нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Примеры  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @y xml (Sales.IndividualSurveySchemaCollection);  
SET @y =  (SELECT TOP 1 Demographics FROM Sales.Individual);  
SELECT @y;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Справочник по языку XQuery (SQL Server)](../../xquery/xquery-language-reference-sql-server.md)  
  
  

