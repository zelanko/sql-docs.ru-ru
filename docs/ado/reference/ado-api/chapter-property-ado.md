---
description: Свойство Chapter (ADO)
title: Свойство Chapter (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ea7810e7b829991d185edf49f8224db57535f947
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975525"
---
# <a name="chapter-property-ado"></a>Свойство Chapter (ADO)
Возвращает или задает OLE DB объект **главы** из объекта [интерфейса адорекордсетконструктион](./adorecordsetconstruction-interface.md) или. При использовании **put_Chapter** для задания объекта **Chapter** подмножество строк преобразуется в объект объекта [набора записей](./recordset-object-ado.md) ADO. Это задает текущую главу объекта **набора строк**. Это свойство доступно для чтения и записи.  
  
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
  
## <a name="applies-to"></a>Применение  
 [Интерфейс ADORecordsetConstruction](./adorecordsetconstruction-interface.md)