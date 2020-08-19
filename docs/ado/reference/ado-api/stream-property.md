---
description: Свойство Stream
title: Свойство потока | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b00d145dfd718c64bbd3a87d6df353114afcb2d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441846"
---
# <a name="stream-property"></a>Свойство Stream
Возвращает или задает OLE DB объект **потока** из или в объекте **адостреамконструктион** .  
  
 Read/write.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>Параметры  
 *ппстреам*  
 Указатель на объект **потока** OLE DB.  
  
 *пстреам*  
 Объект **потока** OLE DB.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойства возвращает стандартные значения HRESULT. Сюда входят S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Применение  
 [Интерфейс ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
