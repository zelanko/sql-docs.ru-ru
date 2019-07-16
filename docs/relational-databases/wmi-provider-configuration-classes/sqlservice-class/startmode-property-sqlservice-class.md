---
title: Свойство StartMode (класс SqlService) | Документация Майкрософт
ms.custom: ''
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
ms.openlocfilehash: e1e8102591eef3976d893ddf0c218b71aa763914
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006854"
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
 Значение = 1. Служба запущена **IoInitSystem** метод. Этот параметр допустим только для служб драйверов.  
  
 Автоматически  
 Значение = 2. Служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Вручную  
 Значение = 3. Служба запускается диспетчером компьютера, когда процесс вызывает **StartService** метод.  
  
 Выключено  
 Значение = 4. Служба не может быть запущена.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
