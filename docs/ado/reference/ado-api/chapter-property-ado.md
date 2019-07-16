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
ms.openlocfilehash: 2791bc1a89f8cec1362ab1f00c3be739f7d56b96
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920105"
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
