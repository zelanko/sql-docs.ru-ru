---
title: Типы данных и XML Массовая загрузка (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95fdeec756a149f0663bfb337eb2103085fb8859
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62717597"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
  Типы данных, заданные в схеме сопоставления (тип XSD, XDR и `sql:datatype`), как правило, пропускаются, за исключением следующих случаев.  
  
 В XSD.  
  
-   Если данные имеют тип `dateTime` или `time`, необходимо задать `sql:datatype`, поскольку в ходе массовой загрузки XML выполняется преобразование данных перед их отправкой в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Когда выполняется Массовая загрузка в столбец `uniqueidentifier` введите [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и значение XSD представляет идентификатор GUID, который включает фигурные скобки ({и}), вам необходимо указать **SQL: DataType = «uniqueidentifier»** Чтобы удалить скобки перед передачей вставляемое в столбец. Если атрибут `sql:datatype` не задан, то значение передается вместе с фигурными скобками и вставка завершается ошибкой.  
  
 Дополнительные сведения о `sql:datatype`, см. в разделе [приведение типов данных и заметка SQL: DataType &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если `dt:type` имеет тип `datetime`, `time`, `dateTime.tz` или `time.tz`, необходимо задать типы данных `dt:type` и `sql:datatype`, поскольку при массовой загрузке XML выполняется преобразование данных перед отправкой в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Если XML-данных имеет тип `uuid`, `sql:datatype` должен быть указан; **DT: Type = «uuid»** также является обязательным, если данные являются строковыми. Если атрибут `dt:uuid` не задан, то при массовой загрузке XML строки с фигурными скобками принимаются (фигурные скобки при необходимости удаляются).  
  
-   Если данные XML имеют тип `bin.base64` или `bin.hex`, необходимо указать тип данных XML с атрибутом `dt:type`. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  
