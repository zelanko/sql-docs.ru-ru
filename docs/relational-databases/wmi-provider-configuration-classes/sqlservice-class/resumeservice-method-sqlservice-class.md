---
title: Метод ResumeService (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ResumeService Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 36ee271b89f707b18ff5a438a8d868048efca864
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784741"
---
# <a name="resumeservice-method-sqlservice-class"></a>Метод ResumeService (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Пытается перевести службу в состояние возобновления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ResumeService()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32 равно 0, если запрос **ResumeService** был принят; равно 1, если запрос не поддерживается; и равно любому другому числу для указания ошибки.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
