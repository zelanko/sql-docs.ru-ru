---
title: "Строка свойства (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19b935d43739d1a1ce19f414cae12b00c311b261
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="row-property-ado"></a>Свойства строки (ADO)
Возвращает или задает поставщика OLE DB **строки** объект из или в [ADORecordConstruction интерфейс](../../../ado/reference/ado-api/adorecordconstruction-interface.md) объекта. При использовании **put_Row** для задания **строки** объекта строки преобразуются в ADO **записи** объекта.  
  
## <a name="readwritesyntax"></a>Чтение и запись. Синтаксис  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Параметры  
 *ppRow*  
 Указатель на OLE DB **строки** объекта.  
  
 *PRow*  
 OLE DB **строки** объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
