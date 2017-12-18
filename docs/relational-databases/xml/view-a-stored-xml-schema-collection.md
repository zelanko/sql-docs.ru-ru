---
title: "Просмотр хранимой коллекции схем XML | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60d143e53c01fb90e4c8c73c42f20463739d185c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="view-a-stored-xml-schema-collection"></a>Просмотр хранимой коллекции схем XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] После импорта коллекции схем XML с помощью инструкции [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md) компоненты схемы хранятся в метаданных. Можно использовать внутреннюю функцию [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md), чтобы повторно построить коллекцию XML-схем. Эта функция возвращает экземпляр типа данных **xml** .  
  
 Например, следующий запрос извлекает коллекцию XML-схем (`ProductDescriptionSchemaCollection`) в реляционной схеме продукции в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Если нужно увидеть только одну схему из коллекции, можно задать запрос XQuery для результата типа **xml** , возвращаемого функцией `xml_schema_namespace`.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 Например, следующий запрос находит сведения об XML-схеме поддержки и гарантий на продукт в коллекции XML-схем `ProductDescriptionSchemaCollection` .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 Также можно передать в качестве необязательного третьего параметра для `xml_schema_namespace` целевое пространство имен, чтобы получить из коллекции конкретную схему, как показано в следующем запросе:  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Когда в базе данных создается коллекция XML-схем с помощью инструкции CREATE XML SCHEMA COLLECTION, она сохраняет компоненты схемы в метаданных. Обратите внимание, что сохраняются только те компоненты схемы, которые понимает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Любые комментарии, заметки или несоответствующие XSD-схеме атрибуты не сохраняются. Следовательно, схема, повторно сконструированная посредством функции **xml_schema_namespace** , функционально эквивалентна первоначальной схеме, но не обязательно будет выглядеть так же. Например, не будет тех же префиксов, которые были в первоначальной схеме. Схема, возвращаемая функцией **xml_schema_namespace** , использует префикс **t** для целевого пространства имен и префиксы **ns1**, **ns2**и так далее для всех остальных.  
  
 Если нужно сохранить точную копию XML-схем, следует сохранить схему в файл или в таблицу базы данных в столбец типа **xml** .  
  
 Представление каталога [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) также возвращает сведения о коллекциях XML-схем. Сюда входят, например сведения об имени коллекции, дате создания и владельце коллекции.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции XML-схем (SQL Server)](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
