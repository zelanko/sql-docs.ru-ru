---
title: Интерфейс IDSOShapeExtensions | Документы Microsoft
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
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0ab928d6ae248acf7dfeafa95755723474c14b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="idsoshapeextensions-interface"></a>Интерфейс IDSOShapeExtensions
Возвращает объект базового источника данных OLE DB для поставщика ФИГУРЫ.  
  
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
|[Метод GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Извлекает объект базового источника данных OLE DB из поставщик Data Shape.|  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздних версий  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
