---
title: "Свойство Глава (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 938eeef6f18e154c4b9c17792f00254934d7cc4b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="chapter-property-ado"></a>Свойство Глава (ADO)
Возвращает или задает поставщика OLE DB **главе** объекта из/в [ADORecordsetConstruction интерфейс](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) объекта. При использовании **put_Chapter** для задания **главе** объекта подмножество строк, преобразуются в ADO [объекта набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. Задает текущий главе **строк**объекта. Это свойство является чтение и запись.  
  
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
 Этот метод свойство возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
