---
description: Свойство Update Resync (динамическое) (ADO)
title: Свойство повторной синхронизации обновлений — Dynamic (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 506fd7fecee179a055e23ffad1beab76bcd2fbe2
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988095"
---
# <a name="update-resync-property-dynamic-ado"></a>Свойство Update Resync (динамическое) (ADO)
Указывает, следует ли за методом [UpdateBatch](./updatebatch-method.md) выполнить неявную операцию повторной [синхронизации](./resync-method.md) , и если да, то область действия этой операции.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно или несколько значений [ADCPROP_UPDATERESYNC_ENUM](./adcprop-updateresync-enum.md) .  
  
## <a name="remarks"></a>Remarks  
 Значения ADCPROP_UPDATERESYNC_ENUM могут быть объединены, за исключением Адресинкалл, который уже представляет сочетание остальных значений.  
  
 Константа **адресинкконфликтс** хранит значения повторной синхронизации в качестве базовых значений, но не переопределяет ожидающие изменения.  
  
 **Повторная синхронизация обновлений** — это динамическое свойство, добавленное к [коллекции свойств](./properties-collection-ado.md) объекта [Recordset](./recordset-object-ado.md) , если свойство [CursorLocation](./cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)