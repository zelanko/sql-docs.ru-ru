---
title: Свойство Chapter (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 601573a34082f386bfee238308a8f97c41743e4b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655422"
---
# <a name="chapter-property-ado"></a>Свойство Chapter (ADO)
Возвращает или задает поставщика OLE DB **глава** объектов или из [интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) объекта. При использовании **put_Chapter** присвоить **глава** объекта, подмножество строк превращается в ADO [объект Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. Таким образом задается в текущем главе **набора строк**объекта. Это свойство доступно для чтения/записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Параметры  
 *plChapter*  
 Указатель на дескриптор главы.  
  
 *LChapter*  
 Дескриптор главы.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая значение S_OK и значение E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
