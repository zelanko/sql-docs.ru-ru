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
ms.openlocfilehash: b2b5fbe59ab58b31cd0b796cbe46963683aa890b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932491"
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
