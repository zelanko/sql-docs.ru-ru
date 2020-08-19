---
description: Метод GetDataProviderDSO
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a45d78960b8b6b1ba2534e39f080a6c94fc0655
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443576"
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
  
## <a name="applies-to"></a>Применяется к  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
