---
title: Метод SetStartMode (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0b3689c843fbbe7ad845a45aca6bb962f8f0c75e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63061962"
---
# <a name="setstartmode-method-sqlservice-class"></a>Метод SetStartMode (класс SqlService)
  Изменяет режим запуска экземпляра службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *StartMode*  
 Значение `uint32`, определяющее режим запуска экземпляра службы.  
  
 Допустимы следующие значения.  
  
 Значение = 0. Загрузка — драйвер устройства запускается загрузчиком операционной системы. Это значение допустимо только для служб драйверов.  
  
 Значение = 1. Загрузка — драйвер устройства запускается методом `IoInitSystem`. Это значение допустимо только для служб драйверов.  
  
 Значение = 2. Автоматически — служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Значение = 3. Вручную — служба запускается оснасткой «Управление компьютером», когда процесс вызывает метод `StartService`.  
  
 Значение = 4. Отключена — служба больше не запускается.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
