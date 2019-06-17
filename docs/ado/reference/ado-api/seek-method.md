---
title: Метод Seek | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 21cb7f8773c0663d584f62bcaaaeab15c7eac108
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711430"
---
# <a name="seek-method"></a>Метод Seek
Выполняет поиск индекса [записей](../../../ado/reference/ado-api/recordset-object-ado.md) можно быстро найти строку, соответствующем заданным значениям и изменяется текущая позиция строки для этой строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Параметры  
 *KeyValues*  
 Массив **Variant** значения. Индекс состоит из одного или нескольких столбцов, и массив содержит значение для сравнения каждого соответствующего столбца.  
  
 *SeekOption*  
 Объект [SeekEnum](../../../ado/reference/ado-api/seekenum.md) значение, которое указывает тип сравнения между столбцами индекса и соответствующий *KeyValues*.  
  
## <a name="remarks"></a>Примечания  
 Используйте **Seek** в сочетании с [индекс](../../../ado/reference/ado-api/index-property.md) свойства, если базовый поставщик поддерживает индексы на **записей** объекта. Используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) **(adSeek)** метод, чтобы определить, поддерживает ли базовый поставщик **Seek**и **Supports(adIndex)** метод, чтобы определить, поддерживает ли поставщик индексов. (Например, [поставщик OLE DB для Jet (Майкрософт)](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) поддерживает **Seek** и **индекс**.)  
  
 Если **Seek** может не найти нужную строку, ошибка не происходит, а эта строка находится в конце **записей**. Задайте **индекс** свойства для заданного индекса до выполнения этого метода.  
  
 Этот метод поддерживается только с курсорами на стороне сервера. Поиск не поддерживается, если **записей** объекта [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойство имеет значение **adUseClient**.  
  
 Этот метод может быть только используется, когда **записей** объект был открыт с [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значение **adCmdTableDirect**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры метода Seek и свойства Index (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Примеры метода Seek и свойства Index (Visual C++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Свойство Index](../../../ado/reference/ado-api/index-property.md)
