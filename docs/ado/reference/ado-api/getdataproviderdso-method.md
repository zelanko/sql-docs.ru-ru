---
title: Метод Жетдатапровидердсо | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932491"
---
# <a name="getdataproviderdso-method"></a>Метод GetDataProviderDSO
Извлекает базовый объект источника данных OLE DB из поставщика фигур.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *ппдатапровидердсоиункновн*  
 заполняет  Указатель на указатель, возвращающий IUnknown базового OLE DB объекта источника данных.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не выполняет AddRef указателя на интерфейс. Если вызывающий объект планирует удерживать указатель, вызывающий объект должен выполнить требуемый метод AddRef и Release.  
  
## <a name="applies-to"></a>Область применения  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
