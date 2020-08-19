---
description: Интерфейс IDSOShapeExtensions
title: Интерфейс Идсошапикстенсионс | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9c7eeb5999a42cfe8b82e570cc5ada1222f87441
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443476"
---
# <a name="idsoshapeextensions-interface"></a>Интерфейс IDSOShapeExtensions
Возвращает базовый объект источника данных OLE DB для поставщика фигур.  
  
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
  
|Метод|Описание|  
|-|-|  
|[Метод GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Извлекает базовый объект источника данных OLE DB из поставщика фигур.|  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2,0 и более поздние версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
