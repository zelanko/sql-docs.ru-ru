---
title: "Свойство RowPosition (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords: RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d3e20769e324400357ea65acc21d338749987ae4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="rowposition-property-ado"></a>Свойство RowPosition (ADO)
Возвращает или задает поставщика OLE DB **RowPosition** объекта из/в **ADORecordsetConstruction** объекта. При использовании **put_RowPosition** для задания **RowPosition** объектов, итоговый **записей** объектов используют **RowPosition** объект Определите текущую строку.  
  
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
 Этот метод свойство возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="remarks"></a>Замечания  
 Если задано это свойство, если **строк** объекта на **RowPosition** объекта отличается от **строк** объекта на **записей**объекта первое переопределяет последний. То же самое относится к текущему **главе** из **RowPosition** также.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
