---
title: 'Использование заметок SQL: IDENTITY и | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b54109b005956241b87efe89a33bf1c949b792e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193330"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Использование заметок sql:identity и sql:guid
  Можно указать `sql:identity` и `sql:guid` заметок в схеме XSD на любой узел, который сопоставляется со столбцом базы данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хотя формат диаграммы обновления поддерживает атрибуты `updg:at-identity` и `updg:guid`, формат дельты их не поддерживает. Атрибут `updg:at-identity` определяет поведение при обновлении столбца с типом IDENTITY. Атрибут `updg:guid` позволяет получить значение идентификатора GUID из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать его в диаграмме обновления. Дополнительные сведения и рабочие образцы см. в разделе [Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Заметки `sql:identity` и `sql:guid` расширяют эту функциональность для дельт.  
  
 При выполнении дельты она вначале преобразуется в диаграмму обновления, а затем выполняется диаграмма обновления. Если задать заметки `sql:identity` и `sql:guid` в схеме XSD, то этим фактически определяется поведение диаграммы обновления. Поэтому все заметки описаны в контексте диаграммы обновления. Заметки можно использовать как для дельт, так и для диаграммы обновления, но диаграммы обновления уже предоставляют более эффективный способ обработки значений идентификаторов и GUID.  
  
 Заметки `sql:identity` и `sql:guid` можно определять в элементе со сложным содержимым.  
  
## <a name="sqlidentity-annotation"></a>Заметка sql:identity  
 Заметку `sql:identity` в схеме XSD можно задать на любом узле, который сопоставляется со столбцом IDENTITY в базе данных. Значение, заданное для этой заметки, определяет способ обновления столбца IDENTITY (или с помощью значения в диаграмме обновления для столбца, или пропуском этого значения, и в этом случае для столбца используется значение, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
 Заметке `sql:identity` могут быть присвоены два значения:  
  
 ignore  
 Дает диаграмме обновления указание не учитывать заданные в ней значения и использовать для столбца значение идентификатора, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 useValue  
 Дает диаграмме обновления указание использовать заданное в ней значение для обновления столбца IDENTITY. Диаграмма обновления не проверяет, имеет ли столбец значение идентификатора.  
  
 Если в диаграмме обновления задано значение для столбца IDENTITY, в схеме необходимо задать `sql:identity="useValue"`.  
  
## <a name="sqlguid-annotation"></a>Заметка sql:guid  
 Диаграмма обновления может предложить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформировать значение идентификатора GUID и затем использовать это значение. В контексте дельты заметку `sql:guid` можно использовать для указания, следует ли применять значение GUID, сформированное SQL Server, или значение диаграммы обновления для этого столбца.  
  
 Заметке `sql:guid` могут быть присвоены два значения:  
  
 generate  
 Указывает, что для операции обновления используется значение GUID, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого столбца.  
  
 useValue  
 Указывает, что для обновления столбца используется значение, заданное в диаграмме обновления. Это значение по умолчанию.  
  
  