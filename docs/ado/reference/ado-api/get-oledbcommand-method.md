---
title: Метод get_OLEDBCommand | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01e6082d17932dfc85e7ce7ca1ecd3f09d69bc5a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="getoledbcommand-method"></a>Метод get_OLEDBCommand
Возвращает базовый Команда OLE DB, сначала распространении информацию параметра для команды ADO для команды OLE DB.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *ppOLEDBCommand*  
 [out] Указатель на положение указателя, который будет записан указатель IUnknown для базовой команды OLE DB.  
  
## <a name="applies-to"></a>Объект применения  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
