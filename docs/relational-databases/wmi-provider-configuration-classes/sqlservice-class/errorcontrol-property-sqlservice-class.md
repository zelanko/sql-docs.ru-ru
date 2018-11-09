---
title: Свойство ErrorControl (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 436c26aa6fffcfc364b47cbfbc8cf3c32e145849
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217582"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Свойство ErrorControl (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает или задает серьезность ошибки, если служба не запускается во время запуска системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
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
  
## <a name="remarks"></a>Примечания  
 Значение задает действие, предпринимаемое программой запуска при возникновении ошибки. Все ошибки записываются в журнал системой компьютера.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
