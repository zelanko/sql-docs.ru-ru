---
title: "CursorTypeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: CursorTypeEnum
helpviewer_keywords: CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5adf070387078902d7d21a68cc0f89af2de8194a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Указывает тип курсора, используемого в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Использует динамический курсор. Добавления, изменения и удаления другими пользователями являются видимыми и все типы перемещения через **записей** разрешены, за исключением закладки, если поставщик не поддерживает их.|  
|**adOpenForwardOnly**|0|По умолчанию. Использует курсор последовательного доступа. Аналогична статический курсор, за исключением того, что прокрутку можно использовать только вперед записей. Это позволяет повысить производительность, если необходимо внести только одно проходят через **записей**.|  
|**adOpenKeyset**|1|Использует курсор набора ключей. Как динамический курсор, за исключением того, что записи, которые добавляют другим пользователям, не отображается, несмотря на то, что записи, которые другие пользователи удаляют недоступны из вашего **записей**. Изменения данных другими пользователями, по-прежнему видны.|  
|**adOpenStatic**|3|Использует статический курсор, который является копией статический набор записей, которые можно использовать для поиска данных или создавать отчеты. Добавления, изменения или удаления другими пользователями не отображаются.|  
|**adOpenUnspecified**|-1|Не указывает тип курсора.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
