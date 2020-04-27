---
title: Свойство AcceptPause (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f28c72a291c145171f7084524fe5dd5cce7c12a0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63223271"
---
# <a name="acceptpause-property-sqlservice-class"></a>Свойство AcceptPause (класс SqlService)
  Возвращает логическое значение свойства, определяющее, можно ли приостановить службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, определяющее, можно ли приостановить службу: `true`, если службу можно приостановить; или `false`, если службу нельзя приостановить.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
