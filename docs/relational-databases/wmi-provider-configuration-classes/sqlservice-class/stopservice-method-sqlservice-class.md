---
title: Метод «не в» (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StopService Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StopService method
ms.assetid: ef8e1856-4930-417a-8f52-be470fd3f15c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3b8a268446517788c35e29b4f86821373a283070
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750050"
---
# <a name="stopservice-method-sqlservice-class"></a>Метод StopService (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Пытается перевести службу в остановленное состояние.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.StopService()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** равно 0, если запрос **ResumeService** был принят; равно 1, если запрос не поддерживается; и равно любому другому числу для указания ошибки.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
