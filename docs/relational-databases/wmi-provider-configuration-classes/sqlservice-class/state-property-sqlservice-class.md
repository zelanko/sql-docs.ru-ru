---
title: Состояние свойство (класс SqlService) | Документы Microsoft
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
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b4c2af75786f0db01c522147645866c3e8786a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="state-property-sqlservice-class"></a>Свойство State (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает или задает текущее состояние службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее состояние службы.  
  
 Может иметь одно из следующих значений.  
  
 1  
 Остановлена. Служба остановлена.  
  
 2  
 Ожидание запуска. Служба ожидает запуска.  
  
 3  
 Ожидание остановки. Служба ожидает остановки.  
  
 4  
 Выполняется. Служба выполняется.  
  
 5  
 Ожидание продолжения. Служба ожидает продолжения.  
  
 6  
 Ожидание приостановки. Служба ожидает приостановки.  
  
 7  
 приостановлено Служба приостановлена.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
