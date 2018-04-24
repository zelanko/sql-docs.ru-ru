---
title: Замена существующих столбцов на столбцы XML | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4946c87365bd886e20ba97fe3b1753e54344f85b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="change-existing-columns-to-xml-columns"></a>Замена существующих столбцов на XML-столбцы
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Инструкция ALTER TABLE поддерживает тип данных **xml** . Например, можно преобразовать столбец любого строкового типа в тип данных **xml** . Учтите, что в этом случае документы, содержащиеся в этом столбце, должны быть корректными. Также при изменении типа столбца со строкового на типизированный xml, содержащиеся в столбце документы должны проходить проверку по указанным XSD-схемам.  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 Можно изменить тип содержащихся в столбце `xml` данных с нетипизированного на типизированный XML. Пример:  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  Cкрипт будет работать с базой данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , потому что коллекция XML-схем `Production.ProductDescriptionSchemaCollection`создана в виде части базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
 В предыдущем примере все сохраненные в столбце экземпляры проверяются на корректность и типизацию в соответствии с XSD-схемами из указанной коллекции. Если столбец содержит хотя бы один экземпляр XML, не проходящий проверку на соответствие указанной схеме, выполнение инструкции `ALTER TABLE` завершится ошибкой, и преобразование нетипизированного XML-столбца в типизированный будет невозможно.  
  
> [!NOTE]  
>  Если таблица имеет большой размер, операция изменения столбца типа **xml** может требовать много ресурсов. Причиной этого является необходимость проверки каждого документа на корректность, а для типизированного XML — также и проверки соответствия схеме.  
  
 Дополнительные сведения о типизированном XML см. в разделе [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
  
