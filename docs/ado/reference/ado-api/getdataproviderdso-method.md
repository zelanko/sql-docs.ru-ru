---
title: "Метод GetDataProviderDSO | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90c18a4c83f556d4283b76c364686e8308d75474
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="getdataproviderdso-method"></a>Метод GetDataProviderDSO
Извлекает объект базового источника данных OLE DB из поставщик Data Shape.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *ppDataProviderDSOIUnknown*  
 [out]  Указатель на указатель, который возвращает IUnknown базового объекта источника данных OLE DB.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не addref не указатель на интерфейс. Если вызывающий объект планирует указатель, вызывающий объект должен выполнять необходимые addref и release.  
  
## <a name="applies-to"></a>Область применения  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
