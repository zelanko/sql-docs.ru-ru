---
title: "Способа | Документы Microsoft"
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
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af29a65772019a31c495fedc546b204e98455809
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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
  
## <a name="remarks"></a>Remarks  
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
