---
title: Свойство ExitCode (класс SqlService) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 07aaad1e95d5c02bbb6f82f3dfa2d26e079372f7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="exitcode-property-sqlservice-class"></a>Свойство ExitCode (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает или задает код ошибки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32, которая определяет проблемы, происходящие при запуске и остановке службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , определяющее код завершения.  
  
## <a name="remarks"></a>Замечания  
 Это свойство имеет значение ERROR_SERVICE_SPECIFIC_ERROR (1066), если ошибка уникальна для службы, представленной этим классом. Во время выполнения и после нормального завершения работы служба присваивает этому параметру значение NO_ERROR.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
