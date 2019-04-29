---
title: Метод get_OLEDBCommand | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 636b2f541ebd5d3624e205a3442cf1618cdf78a6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028171"
---
# <a name="getoledbcommand-method"></a>Метод get_OLEDBCommand
Возвращает базовый Команда OLE DB, сначала передавать трафик транзитом через любые сведения о параметрах на ADO в команду OLE DB.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *ppOLEDBCommand*  
 [out] Указатель на указатель на расположение, куда будет записан указатель IUnknown для базовой команды OLE DB.  
  
## <a name="applies-to"></a>Объект применения  
 [IADOCommandConstruction](https://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
