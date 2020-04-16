---
title: Использование заметок sql:identity и sql:guid
description: Узнайте, как использовать sql:identity и sql:guid аннотации в схеме XSD для определения поведения xML-обновления.
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
ms.openlocfilehash: f581c1a5c0d925d48df5a16d95cdb141e2d48f83
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388108"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Использование заметок sql:identity и sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Вы можете указать **sql:идентификационные** и **sql:guid** аннотации в схеме XSD на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]любом узеле, который отображает сят в столбце базы данных в . В то время как формат updategram поддерживает **updg: at-identity** и **updg:guid** атрибуты, формат DiffGram не делает. Атрибут **updg:at-identity** определяет поведение при обновлении столбца типа IDENTITY. Атрибут **updg:guid** позволяет получить значение GUID [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать его в updategram. Для получения дополнительной информации и рабочих образцов, см [Вставка данных С помощью XML Updategrams &#40;S'LXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 **Аннотации sql:identity** и **sql:guid** расширяют эту функциональность на DiffGrams.  
  
 При выполнении дельты она вначале преобразуется в диаграмму обновления, а затем выполняется диаграмма обновления. Указывая **sql:идентификационные** и **sql:guid** аннотации в схеме XSD, вы на самом деле определения поведения updategram. Поэтому все заметки описаны в контексте диаграммы обновления. Заметки можно использовать как для дельт, так и для диаграммы обновления, но диаграммы обновления уже предоставляют более эффективный способ обработки значений идентификаторов и GUID.  
  
 Аннотации **sql:identity** и **sql:guid** можно определить на элементе сложного содержимого.  
  
## <a name="sqlidentity-annotation"></a>Заметка sql:identity  
 Аннотацию **sql:идентификация** в схеме XSD можно указать на любом узеле, который отображается в столбце базы данных типа IDENTITY. Значение, указанное для этой аннотации, определяет, как обновляется столбец типа IDENTITY (либо с помощью значения, указанного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в обновлении, для изменения столбца, либо путем игнорирования значения, и в этом случае для этого столбца используется генерируемое значение.  
  
 Аннотации **кв/м:идентификация** может быть присвоена двум значениям:  
  
 ignore  
 Дает диаграмме обновления указание не учитывать заданные в ней значения и использовать для столбца значение идентификатора, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 useValue  
 Дает диаграмме обновления указание использовать заданное в ней значение для обновления столбца IDENTITY. Диаграмма обновления не проверяет, имеет ли столбец значение идентификатора.  
  
 Если в обновлении указывается значение для столбца типа IDENTITY, в схеме должна быть указана **sql:identity-"useValue".**  
  
## <a name="sqlguid-annotation"></a>Заметка sql:guid  
 Диаграмма обновления может предложить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформировать значение идентификатора GUID и затем использовать это значение. В контексте DiffGrams можно использовать аннотацию **sql:guid,** чтобы указать, следует ли использовать значение GUID, генерируемое сервером S'L, или использовать значение, которое предусмотрено в этой колонке.  
  
 Аннотации **sql:guid** можно присвоить два значения:  
  
 generate  
 Указывает, что для операции обновления используется значение GUID, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого столбца.  
  
 useValue  
 Указывает, что для обновления столбца используется значение, заданное в диаграмме обновления. Это значение по умолчанию.  
  
  
