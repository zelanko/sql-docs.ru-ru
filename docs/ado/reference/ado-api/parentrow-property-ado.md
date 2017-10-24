---
title: "Свойство ParentRow (ADO) | Документы Microsoft"
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
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 52b23aa90e3a2e0998547849d71c3c10a3e0552d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="parentrow-property-ado"></a>Свойство ParentRow (ADO)
Задает контейнер OLE DB **строки** объекта на **ADORecordConstruction** объекта, чтобы родительские строки преобразуются в ADO **записи** объекта.  
  
 Доступный только на запись.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Параметры  
 *pParent*  
 Контейнер строки.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)

