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
manager: craigg
ms.openlocfilehash: 0c7d864d61d2782955a52ce6e20a7025379cc946
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028073"
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
