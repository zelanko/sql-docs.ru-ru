---
title: Свойство ConnectionString (класс SqlServerAlias) | Документы Microsoft
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
- ConnectionString Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- ConnectionString property
ms.assetid: 8a3692b9-3a34-42e2-b0b9-28e6bd3a7aba
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95950cbd1f5c68bf2f192dc096a823805d0985e1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="connectionstring-property-sqlserveralias-class"></a>Свойство ConnectionString (класс SqlServerAlias)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает строку соединения, которая используется при установке соединения для псевдонима соединения сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ConnectionString [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , представляющий псевдоним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строка, определяющая строку соединения, которая используется при установке соединения для псевдонима соединения сервера.  
  
## <a name="remarks"></a>Замечания  
  
