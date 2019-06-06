---
title: Свойство ParentRow (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 180ab01d28cb5c6f7715480459eeb12ab6ea81be
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703290"
---
# <a name="parentrow-property-ado"></a>Свойство ParentRow (ADO)
Задает контейнер объекта OLE DB **строки** объект **ADORecordConstruction** объекта, таким образом, чтобы строки родительский превращается в ADO **записи** объекта.  
  
 Доступный только на запись.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Параметры  
 *pParent*  
 Контейнер строки.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая значение S_OK и значение E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
