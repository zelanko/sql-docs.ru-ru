---
title: Свойство AcceptStop (класс SqlService) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- AcceptStop Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 57e8a60b431ad0a5f24ad01d3d3536642fe3887a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="acceptstop-property-sqlservice-class"></a>Свойство AcceptStop (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает логическое значение, определяющее, можно ли остановить службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AcceptStop [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класс SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) объект, представляющий службу  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, указывающее, возможен ли останов службы: **true** при остановке службы или **false** остановки службы.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
