---
title: Свойство StartMode (класс SqlService) | Документы Microsoft
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
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93802c3cc0e53b0996bd7db5d5a6bca959c4302a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="startmode-property-sqlservice-class"></a>Свойство StartMode (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает режим запуска службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее режим службы.  
  
 Может иметь одно из следующих значений.  
  
 Загрузка  
 Значение = 0. Служба запускается загрузчиком операционной системы. Этот параметр допустим только для служб драйверов.  
  
 System  
 Значение = 1. Служба запускается методом **IoInitSystem** метод. Этот параметр допустим только для служб драйверов.  
  
 Автоматически  
 Значение = 2. Служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Вручную  
 Значение = 3. Служба запускается оснасткой Управление компьютером, когда процесс вызывает **StartService** метод.  
  
 Выключено  
 Значение = 4. Служба не может быть запущена.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
