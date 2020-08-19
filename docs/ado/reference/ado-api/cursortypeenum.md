---
description: CursorTypeEnum
title: Курсортипинум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: beb6afdd93d69ea920acee3840dc6c0bc44d181e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444246"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Указывает тип курсора, используемого в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Использует динамический курсор. Видимыми могут быть дополнения, изменения и удаления других пользователей, а также все типы перемещений через **набор записей** , за исключением закладок, если они не поддерживаются поставщиком.|  
|**адопенфорвардонли**|0|По умолчанию. Использует однопроходный курсор. Идентичен статическому курсору, за исключением того, что можно прокручивать только записи вперед. Это повышает производительность, если необходимо выполнить только один проход по **набору записей**.|  
|**adOpenKeyset**|1|Использует курсор KEYSET. Как и динамический курсор, за исключением того, что вы не можете видеть записи, добавленные другими пользователями, хотя записи, удаляемые другими пользователями, недоступны из **набора записей**. Изменения данных, внесенные другими пользователями, по-прежнему видимы.|  
|**adOpenStatic**|3|Использует статический курсор, который представляет собой статическую копию набора записей, которые можно использовать для поиска данных или создания отчетов. Добавление, изменение или удаление других пользователей не отображается.|  
|**адопенунспеЦифиед**|-1|Не указывает тип курсора.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. примеры CursorType. DYNAMIC|  
|Адоенумс. примеры CursorType. ФОРВАРДОНЛИ|  
|Адоенумс. примеры CursorType. KEYSET|  
|Адоенумс. примеры CursorType. STATIC|  
|Адоенумс. примеры CursorType. не указано|  
  
## <a name="applies-to"></a>Применение  
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
