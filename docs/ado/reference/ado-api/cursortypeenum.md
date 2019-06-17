---
title: CursorTypeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: dd3469b826ac4f577ff0e883b1a92a3acec4a981
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698533"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Указывает тип курсора, используемого в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Использует динамический курсор. Добавления, изменения и удаления другими пользователями видимы, но и все типы перемещения с помощью **записей** допускается, за исключением закладки, если поставщик не поддерживает их.|  
|**adOpenForwardOnly**|0|По умолчанию. Использует курсор последовательного доступа. Совпадает с статический курсор, за исключением того, что вы можете только прокрутку вперед записей. Это повышает производительность, когда необходимо внести только одно, которые проходят через **записей**.|  
|**adOpenKeyset**|1|Использует курсор набора ключей. За исключением того, что несмотря на то, что записи, которые другие пользователи удаляют недоступны из записей, добавить других пользователей, не отображается, такие как динамический курсор, ваш **записей**. Изменения данных другие пользователи по-прежнему отображаются.|  
|**adOpenStatic**|3|Использует статический курсор, который является копией статический набор записей, которые можно использовать для поиска данных или создавать отчеты. Дополнения, изменения или удаления других пользователей не отображаются.|  
|**adOpenUnspecified**|-1|Не указан тип курсора.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
