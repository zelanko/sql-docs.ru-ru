---
title: Свойство повторной синхронизации обновлений — Dynamic (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d000150cc86a8c838ac5dea827b5c376f3a79f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759490"
---
# <a name="update-resync-property-dynamic-ado"></a>Свойство Update Resync (динамическое) (ADO)
Указывает, следует ли за методом [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) выполнить неявную операцию повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md) , и если да, то область действия этой операции.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно или несколько значений [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) .  
  
## <a name="remarks"></a>Remarks  
 Значения ADCPROP_UPDATERESYNC_ENUM могут быть объединены, за исключением Адресинкалл, который уже представляет сочетание остальных значений.  
  
 Константа **адресинкконфликтс** хранит значения повторной синхронизации в качестве базовых значений, но не переопределяет ожидающие изменения.  
  
 **Повторная синхронизация обновлений** — это динамическое свойство, добавленное к [коллекции свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , если свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
