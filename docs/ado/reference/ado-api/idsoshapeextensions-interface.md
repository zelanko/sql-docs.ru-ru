---
title: Интерфейс IDSOShapeExtensions | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36f91ea537b1ad2a5e52221400f41bf88dc544b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028041"
---
# <a name="idsoshapeextensions-interface"></a>Интерфейс IDSOShapeExtensions
Получает в базовом объекте источника данных OLE DB для поставщика ФИГУРЫ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
interface IDSOShapeExtensions: public IUnknown {  
public:  
      HRESULT  GetDataProviderDSO(  
            IUnknown **ppDataProviderDSOIUnknown  
      );  
};  
```  
  
## <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[Метод GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|В базовом объекте источника данных OLE DB извлекает из поставщик Data Shape.|  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздние версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
