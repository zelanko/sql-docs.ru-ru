---
title: Свойство ErrorControl (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 83955510a18a2fbc77be5aeb7005704852f0e4a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135884"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Свойство ErrorControl (класс SqlService)
  Возвращает или задает серьезность ошибки, если служба не запускается во время запуска системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
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
  
## <a name="remarks"></a>Примечания  
 Значение задает действие, предпринимаемое программой запуска при возникновении ошибки. Все ошибки записываются в журнал системой компьютера.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
