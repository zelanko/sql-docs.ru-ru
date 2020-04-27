---
title: Свойство Row (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 134f5fe05f89d6c8662a68f9f782f460c4b5f0aa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917117"
---
# <a name="row-property-ado"></a>Свойство Row (ADO)
Возвращает или задает объект OLE DB **строки** из объекта [интерфейса адорекордконструктион](../../../ado/reference/ado-api/adorecordconstruction-interface.md) или. При использовании **put_Row** для задания объекта **строки** строка преобразуется в объект **записи** ADO.  
  
## <a name="readwritesyntax"></a>Чтение и запись. Syntax  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Параметры  
 *ппров*  
 Указатель на объект **строки** OLE DB.  
  
 *пров*  
 Объект **строки** OLE DB.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойства возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Применяется к  
 [Интерфейс ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
