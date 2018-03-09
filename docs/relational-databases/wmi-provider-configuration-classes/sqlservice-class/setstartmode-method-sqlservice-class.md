---
title: "Метод SetStartMode (класс SqlService) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 713513ec867a8d5dadf46a59a0721eea10d26919
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="setstartmode-method-sqlservice-class"></a>Метод SetStartMode (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Изменяет режим запуска экземпляра службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *StartMode*  
 Значение **uint32** , определяющее режим запуска экземпляра службы.  
  
 Допустимы следующие значения.  
  
 Значение = 0. Загрузка — драйвер устройства запускается загрузчиком операционной системы. Это значение допустимо только для служб драйверов.  
  
 Значение = 1. Загрузка — драйвер устройства запускается методом **IoInitSystem** . Это значение допустимо только для служб драйверов.  
  
 Значение = 2. Автоматически — служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Значение = 3. Вручную — служба запускается оснасткой «Управление компьютером», когда процесс вызывает метод **StartService** .  
  
 Значение = 4. Отключена — служба больше не запускается.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
