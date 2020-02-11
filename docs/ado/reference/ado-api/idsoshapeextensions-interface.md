---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: deca1648d6ef4f9ba3a1dfd020dc5193c8cc0d25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932425"
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
  
|||  
|-|-|  
|[Метод GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Извлекает базовый объект источника данных OLE DB из поставщика фигур.|  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2,0 и более поздние версии  
  
 **Библиотека:** Msado15. dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
