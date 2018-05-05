---
title: Способа | Документы Microsoft
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
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59dcdd3426c39449b3d2348218aa7794a75c0474
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="seek-method"></a>Метод поиска
Выполняет поиск индекса [записей](../../../ado/reference/ado-api/recordset-object-ado.md) быстро найти строку, соответствующем заданным значениям и изменяет текущую позицию строки для этой строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Параметры  
 *KeyValues*  
 Массив **Variant** значения. Индекс состоит из одного или нескольких столбцов, и массив содержит значение для сравнения каждого соответствующего столбца.  
  
 *SeekOption*  
 Объект [SeekEnum](../../../ado/reference/ado-api/seekenum.md) значение, которое указывает тип сравнения между столбцами индекса и соответствующие *KeyValues*.  
  
## <a name="remarks"></a>Замечания  
 Используйте **Seek** в сочетании с [индекс](../../../ado/reference/ado-api/index-property.md) свойства, если базовый поставщик поддерживает индексы на **записей** объекта. Используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** метод, чтобы определить, поддерживает ли базовый поставщик **Seek**и **Supports(adIndex)** метод, чтобы определить, поддерживает ли поставщик индексов. (Например, [поставщик OLE DB для Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) поддерживает **Seek** и **индекс**.)  
  
 Если **Seek** может не найти нужную строку ошибки не возникает и строка располагается в конце **записей**. Задать **индекс** свойства в нужный индекс перед выполнением этого метода.  
  
 Этот метод поддерживается только для серверных курсоров. Поиск не поддерживается, если **записей** объекта [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) значение свойства **adUseClient**.  
  
 Этот метод можно использовать, когда **набора записей** объект был открыт с [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значение **adCmdTableDirect**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Поиск метода и пример свойства индекса (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Поиск метода и пример свойства индекса (VC ++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find-метод (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Свойство Index](../../../ado/reference/ado-api/index-property.md)
