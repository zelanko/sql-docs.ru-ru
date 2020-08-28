---
description: Свойство RowPosition (ADO)
title: Свойство Ровпоситион (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5072555e07a9fafb70b90a1bc19fa06f12c17d45
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989385"
---
# <a name="rowposition-property-ado"></a>Свойство RowPosition (ADO)
Возвращает или задает OLE DB объект **ровпоситион** из или в объекте **адорекордсетконструктион** . При использовании **put_RowPosition** для задания объекта **ровпоситион** результирующий объект **набора записей** использует объект **ровпоситион** для определения текущей строки.  
  
 Read/write.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Параметры  
 *ппровпос*  
 Указатель на объект OLE DB **ровпоситион** .  
  
 *провпос*  
 Объект OLE DB **ровпоситион** .  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойства возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="remarks"></a>Remarks  
 Если это свойство задано, то если объект **набора строк** в объекте **ровпоситион** отличается от объекта набора **строк** в объекте **набора записей** , первый из них переопределяется последним. Такое же поведение применимо и к текущей **главе** **ровпоситион** .  
  
## <a name="applies-to"></a>Применение  
 [Интерфейс ADORecordsetConstruction](./adorecordsetconstruction-interface.md)