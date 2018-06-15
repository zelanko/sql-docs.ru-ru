---
title: Обновить повторной синхронизации свойство динамические (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae21cd46a181a3541dedb663dafef845ec162930
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282690"
---
# <a name="update-resync-property-dynamic-ado"></a>Свойство динамической повторной синхронизации обновления (ADO)
Указывает ли [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод следуют неявный [Resync](../../../ado/reference/ado-api/resync-method.md) метод операцию и если да, область данной операции.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает один или несколько [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) значения.  
  
## <a name="remarks"></a>Примечания  
 Значения ADCPROP_UPDATERESYNC_ENUM могут объединяться, за исключением adResyncAll, который уже представляет сочетание другими значениями.  
  
 Константа **adResyncConflicts** сохраняет значения повторной синхронизации в качестве базового значения, но не переопределяет ожидающих изменений.  
  
 **Обновить повторной синхронизации** динамическое свойство добавляется к [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
