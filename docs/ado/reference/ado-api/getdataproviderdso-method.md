---
title: Метод GetDataProviderDSO | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 687ba2301edfbd944bc9feafdbce2c528b26b58c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Этот метод не addref не указатель на интерфейс. Если вызывающий объект планирует указатель, вызывающий объект должен выполнять необходимые addref и release.  
  
## <a name="applies-to"></a>Область применения  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
