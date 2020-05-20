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
author: rothja
ms.author: jroth
ms.openlocfilehash: 55272fdbcd0aacfc8e98cb4e38ae19270b3b461a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760050"
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
  
## <a name="remarks"></a>Примечания  
 Этот метод не выполняет AddRef указателя на интерфейс. Если вызывающий объект планирует удерживать указатель, вызывающий объект должен выполнить требуемый метод AddRef и Release.  
  
## <a name="applies-to"></a>Применяется к  
 [Интерфейс IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
