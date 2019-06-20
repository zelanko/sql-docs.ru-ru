---
title: Метод GetDataProviderDSO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5187e8f9fdce65b8e746a4a18a353462bb353d4f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698037"
---
# <a name="getdataproviderdso-method"></a>Метод GetDataProviderDSO
В базовом объекте источника данных OLE DB извлекает из поставщик Data Shape.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *ppDataProviderDSOIUnknown*  
 [out]  Указатель на указатель, который возвращает IUnknown в базовом объекте источника данных OLE DB.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не выполняет не addref указатель интерфейса. Если вызывающий объект планирует указатель, вызывающий объект должен выполнить необходимые addref и release.  
  
## <a name="applies-to"></a>Применение  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
