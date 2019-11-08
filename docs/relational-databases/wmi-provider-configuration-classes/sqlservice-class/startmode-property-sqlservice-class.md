---
title: Свойство StartMode (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 31d2a413aa606bc6b7065126668fdeabdfacd7b1
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73660871"
---
# <a name="startmode-property-sqlservice-class"></a>Свойство StartMode (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает режим запуска службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее режим службы.  
  
 Может иметь одно из следующих значений.  
  
 Загрузка  
 Значение = 0. Служба запускается загрузчиком операционной системы. Этот параметр допустим только для служб драйверов.  
  
 Система  
 Значение = 1. Служба, запущенная методом **иоинитсистем** . Этот параметр допустим только для служб драйверов.  
  
 Автоматически  
 Значение = 2. Служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Вручную  
 Значение = 3. Служба, запускаемая диспетчером компьютера, когда процесс вызывает метод **StartService** .  
  
 Выключено  
 Значение = 4. Служба не может быть запущена.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также раздел  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
