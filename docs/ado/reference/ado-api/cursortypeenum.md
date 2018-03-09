---
title: "CursorTypeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e58e1d7660b4bcd014d5e4b80226fc9c3cfb293
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Указывает тип курсора, используемого в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
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
