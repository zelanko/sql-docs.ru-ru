---
title: Замена существующих столбцов на столбцы XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 69be783360a3b72cec7edb4c9ecb8f8d9d2cc50a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096444"
---
# <a name="change-existing-columns-to-xml-columns"></a>Замена существующих столбцов на XML-столбцы
  Инструкция ALTER TABLE поддерживает `xml` тип данных. Например, можно изменить столбец любого строкового типа `xml` тип данных. Учтите, что в этом случае документы, содержащиеся в этом столбце, должны быть корректными. Также при изменении типа столбца со строкового на типизированный xml, содержащиеся в столбце документы должны проходить проверку по указанным XSD-схемам.  
  
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
  
 Можно изменить тип содержащихся в столбце `xml` данных с нетипизированного на типизированный XML. Например:  
  
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
>  Если таблица имеет большой размер, операция изменения `xml` столбец типа может требовать много ресурсов. Причиной этого является необходимость проверки каждого документа на корректность, а для типизированного XML — также и проверки соответствия схеме.  
  
 Дополнительные сведения о типизированном XML см. в разделе [Сравнение типизированного и нетипизированного XML](compare-typed-xml-to-untyped-xml.md).  
  
  