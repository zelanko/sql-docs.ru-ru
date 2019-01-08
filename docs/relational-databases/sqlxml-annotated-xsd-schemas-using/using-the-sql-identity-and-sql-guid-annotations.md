---
title: 'Использование заметок SQL: IDENTITY и | Документация Майкрософт'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 611e202007fb9a5b9438e3432984c3722e264bd7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52522865"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Использование заметок sql:identity и sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно указать **: Identity** и **sql:guid** заметок в схеме XSD на любом узле, который сопоставляется со столбцом базы данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В то время как формат диаграммы обновления поддерживает **updg: в identity** и **updg: GUID** атрибуты, не поддерживает формат DiffGram. **Updg: в identity** атрибута определяет поведение при обновлении столбцом типа IDENTITY. **Updg: GUID** атрибут позволяет получить значение идентификатора GUID из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать его в диаграмме обновления. Дополнительные сведения и рабочие образцы см. в разделе [Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 **: Identity** и **sql:guid** заметок расширяют эту функциональность для дельт.  
  
 При выполнении дельты она вначале преобразуется в диаграмму обновления, а затем выполняется диаграмма обновления. Путем указания **: Identity** и **sql:guid** заметок в схеме XSD, являются фактически определяется поведение диаграммы обновления. Поэтому все заметки описаны в контексте диаграммы обновления. Заметки можно использовать как для дельт, так и для диаграммы обновления, но диаграммы обновления уже предоставляют более эффективный способ обработки значений идентификаторов и GUID.  
  
 **: Identity** и **sql:guid** заметки могут быть определены в элементе со сложным содержимым.  
  
## <a name="sqlidentity-annotation"></a>Заметка sql:identity  
 Можно указать **: Identity** заметки в схеме XSD на любой узел, который сопоставляется со столбцом типа IDENTITY базы данных. Значение, заданное для этой аннотации определяет способ обновления столбца IDENTITY (или с помощью значения в диаграмме обновления для изменения этого столбца или пропуском этого значения в этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-сформированное значение используется для этого столбца).  
  
 **: Identity** заметки могут быть присвоены два значения:  
  
 ignore  
 Дает диаграмме обновления указание не учитывать заданные в ней значения и использовать для столбца значение идентификатора, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 useValue  
 Дает диаграмме обновления указание использовать заданное в ней значение для обновления столбца IDENTITY. Диаграмма обновления не проверяет, имеет ли столбец значение идентификатора.  
  
 Если диаграмма обновления указывает значение для столбца типа IDENTITY, **: IDENTITY = «useValue»** должен быть указан в схеме.  
  
## <a name="sqlguid-annotation"></a>Заметка sql:guid  
 Диаграмма обновления может предложить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформировать значение идентификатора GUID и затем использовать это значение. В контексте дельты, можно использовать **sql:guid** заметки, укажите, следует ли использовать значение идентификатора GUID, сформированный сервером SQL или использовать значение, которое предоставляется в диаграмме обновления для этого столбца.  
  
 **Sql:guid** заметки могут быть присвоены два значения:  
  
 generate  
 Указывает, что для операции обновления используется значение GUID, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого столбца.  
  
 useValue  
 Указывает, что для обновления столбца используется значение, заданное в диаграмме обновления. Это значение по умолчанию.  
  
  
