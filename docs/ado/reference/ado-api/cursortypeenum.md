---
title: CursorTypeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ffab8fe9649ce3c48bba686297c14b98aece7310
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
