---
title: Свойство ErrorControl (класс SqlService) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a5dc8a89c6f29045281d33d3c60fdbf1f515e9b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="errorcontrol-property-sqlservice-class"></a>Свойство ErrorControl (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает или задает серьезность ошибки, если служба не запускается во время запуска системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее серьезность ошибки, если служба не запускается во время запуска системы. В следующей таблице приводятся возможные значения.  
  
 Ignore  
 Пользователь не получает уведомление.  
  
 Нормальный  
 Пользователь получает уведомление.  
  
 Severe  
 Система перезапускается в последней известной рабочей конфигурации.  
  
 Критическая  
 Попытка перезапустить систему в рабочей конфигурации.  
  
 Неизвестно  
 Серьезность ошибки неизвестна.  
  
## <a name="remarks"></a>Замечания  
 Значение задает действие, предпринимаемое программой запуска при возникновении ошибки. Все ошибки записываются в журнал системой компьютера.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
