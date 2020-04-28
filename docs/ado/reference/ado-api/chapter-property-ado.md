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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920105"
---
# <a name="chapter-property-ado"></a>Свойство Chapter (ADO)
Возвращает или задает OLE DB объект **главы** из объекта [интерфейса адорекордсетконструктион](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) или. При использовании **put_Chapter** для задания объекта **Chapter** подмножество строк преобразуется в объект объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) ADO. Это задает текущую главу объекта **набора строк**. Это свойство доступно для чтения и записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Параметры  
 *плчаптер*  
 Указатель на маркер главы.  
  
 *лчаптер*  
 Маркер главы.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойства возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Применяется к  
 [Интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
