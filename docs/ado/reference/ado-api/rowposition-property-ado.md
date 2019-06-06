---
title: Свойство RowPosition (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fad2ee85ef40431a6a4e16814f4711404c851d3f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711457"
---
# <a name="rowposition-property-ado"></a>Свойство RowPosition (ADO)
Возвращает или задает поставщика OLE DB **RowPosition** объектов или из **ADORecordsetConstruction** объекта. При использовании **put_RowPosition** присвоить **RowPosition** объект, полученный в результате **записей** объектов используют **RowPosition** объект Определите текущую строку.  
  
 Read/write.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Параметры  
 *ppRowPos*  
 Указатель на OLE DB **RowPosition** объекта.  
  
 *PRowPos*  
 OLE DB **RowPosition** объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая значение S_OK и значение E_FAIL.  
  
## <a name="remarks"></a>Примечания  
 Если задано это свойство, если **набора строк** объект **RowPosition** объекта отличается от **набора строк** объект **записей**объекта, первое из них переопределяет последний. То же самое относится к текущему **глава** из **RowPosition** также.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
