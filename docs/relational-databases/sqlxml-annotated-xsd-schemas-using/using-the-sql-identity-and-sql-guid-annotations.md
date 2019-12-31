---
title: Использование заметок sql:identity и sql:guid
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 50483d7f6f84371b42bf0c79fbc74a1f85a65eab
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246822"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Использование заметок sql:identity и sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно указать заметки **SQL: Identity** и **SQL: GUID** в схеме XSD на любом узле, сопоставленном со столбцом базы данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В то время как формат Диаграмма обновления поддерживает атрибуты **атрибута updg: at-identity** и **атрибута updg: GUID** , Формат DiffGram не имеет значение. Атрибут **атрибута updg: at-identity** определяет поведение при обновлении СТОЛБЦА типа Identity. Атрибут **атрибута updg: GUID** позволяет получить значение GUID из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать его в диаграмма обновления. Дополнительные сведения и рабочие образцы см. в статье [Вставка данных с помощью XML диаграмм обновления &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Заметки **SQL: Identity** и **SQL: GUID** расширяют эту функцию на дельтами.  
  
 При выполнении дельты она вначале преобразуется в диаграмму обновления, а затем выполняется диаграмма обновления. Указав заметки **SQL: Identity** и **SQL: GUID** в схеме XSD, вы фактически определяете поведение диаграмма обновления. Поэтому все заметки описаны в контексте диаграммы обновления. Заметки можно использовать как для дельт, так и для диаграммы обновления, но диаграммы обновления уже предоставляют более эффективный способ обработки значений идентификаторов и GUID.  
  
 Заметки **SQL: Identity** и **SQL: GUID** могут быть определены для сложного элемента содержимого.  
  
## <a name="sqlidentity-annotation"></a>Заметка sql:identity  
 Заметку **SQL: Identity** в схеме XSD можно указать на любом узле, который сопоставляется со столбцом базы данных типа Identity. Значение, заданное для этой заметки, определяет способ обновления столбца типа IDENTITY (либо с помощью значения, указанного в диаграмма обновления для изменения столбца, либо путем игнорирования значения, в этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]для этого столбца используется созданное значение).  
  
 Заметке **SQL: Identity** может быть присвоено два значения:  
  
 ignore  
 Дает диаграмме обновления указание не учитывать заданные в ней значения и использовать для столбца значение идентификатора, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 useValue  
 Дает диаграмме обновления указание использовать заданное в ней значение для обновления столбца IDENTITY. Диаграмма обновления не проверяет, имеет ли столбец значение идентификатора.  
  
 Если диаграмма обновления указывает значение для столбца типа IDENTITY, в схеме должен быть указан **SQL: Identity = "усевалуе"** .  
  
## <a name="sqlguid-annotation"></a>Заметка sql:guid  
 Диаграмма обновления может предложить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформировать значение идентификатора GUID и затем использовать это значение. В контексте дельтами можно использовать аннотацию **SQL: GUID** , чтобы указать, следует ли использовать значение GUID, формируемое SQL Server, или использовать значение, указанное в диаграмма обновления для этого столбца.  
  
 Заметке **SQL: GUID** можно присвоить два значения:  
  
 generate  
 Указывает, что для операции обновления используется значение GUID, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого столбца.  
  
 useValue  
 Указывает, что для обновления столбца используется значение, заданное в диаграмме обновления. Это значение по умолчанию.  
  
  
