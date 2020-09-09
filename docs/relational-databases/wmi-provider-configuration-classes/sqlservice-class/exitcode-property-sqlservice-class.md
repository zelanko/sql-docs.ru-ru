---
description: Свойство ExitCode (класс SqlService)
title: Свойство ExitCode (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 71e5fbe4180c67560709f004ba099bb90ca83b02
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542859"
---
# <a name="exitcode-property-sqlservice-class"></a>Свойство ExitCode (класс SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает или задает код ошибки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32, которая определяет проблемы, происходящие при запуске и остановке службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , определяющее код завершения.  
  
## <a name="remarks"></a>Примечания  
 Это свойство имеет значение ERROR_SERVICE_SPECIFIC_ERROR (1066), если ошибка уникальна для службы, представленной этим классом. Во время выполнения и после нормального завершения работы служба присваивает этому параметру значение NO_ERROR.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
