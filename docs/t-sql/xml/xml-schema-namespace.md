---
title: "XML_SCHEMA_NAMESPACE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_namespace_TSQL
- xml_schema_namespace
dev_langs:
- TSQL
helpviewer_keywords:
- XML schema collections [SQL Server], reconstructing schemas
- xml_schema_namespace function
- reconstructing schemas
- schemas [SQL Server], XML
- schema collections [SQL Server], reconstructing schemas
ms.assetid: ee9873d8-dd3a-4bff-a10c-68bbadbdf1a6
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 449e545672192baa9d16204afe1fb23497959094
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xmlschemanamespace"></a>xml_schema_namespace
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перестраивает все схемы или определенную схему в указанной коллекции XML-схем. Эта функция возвращает экземпляр типа данных **xml** .  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xml_schema_namespace( Relational_schema , XML_schema_collection_name , [ Namespace ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Relational_schema*  
 Имя реляционной схемы. *Relational_schema* — **sysname**.  
  
 *XML_schema_collection_name*  
 Имя коллекции XML-схем, которую необходимо перестроить. *XML_schema_collection_name* — **sysname**.  
  
 *Пространство имен*  
 URI пространства имен XML-схемы, которую требуется перестроить. Максимальная длина — 1000 символов. Если URI пространства имен не предоставлен, перестраивается вся коллекция XML-схем. *Пространство имен* — **nvarchar(4000)**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **xml**  
  
## <a name="remarks"></a>Замечания  
 При импорте компонентов XML-схемы в базе данных с использованием [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md) или [ALTER XML SCHEMA COLLECTION](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md), сохраняются характеристики схемы, используемой для проверки. Поэтому перестроенная схема лексически может отличаться от исходного документа схемы. В частности, теряются комментарии, пробельные символы и заметки, а также данные неявных типов преобразуются в явные. Например \<xs: element name = «e1» / > становится \<xs: element name = «e1» type = «xs: anyType» / >. Кроме этого, префиксы пространства имен не сохраняются.  
  
 Если указан параметр пространства имен, в результирующем документе схемы будут содержаться определения для всех компонентов схемы в этом пространстве имен, даже если они были добавлены в других документах схемы или во время выполнения этапов языка DDL (или если имели место оба случая).  
  
 Эту функцию нельзя использовать для создания документов схемы XML из **sys.sys** коллекции XML-схем.  
  
## <a name="examples"></a>Примеры  
 В следующем примере коллекция XML-схем `ProductDescriptionSchemaCollection` запрашивается из производственной реляционной схемы в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT xml_schema_namespace(N'production',N'ProductDescriptionSchemaCollection');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Просмотр хранимой коллекции схем XML](../../relational-databases/xml/view-a-stored-xml-schema-collection.md)   
 [Коллекции XML-схем (SQL Server)](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  

