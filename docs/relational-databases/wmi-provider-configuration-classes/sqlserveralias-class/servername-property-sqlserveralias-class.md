---
title: Свойство ServerName (класс SqlServerAlias) | Документы Microsoft
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
- ServerName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a38f23a47ecd6e08ec2f0bf54845922a2d86761
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="servername-property-sqlserveralias-class"></a>Свойство ServerName (класс SqlServerAlias)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает имя экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , заданного псевдонимом соединения сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ServerName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , представляющий псевдоним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на который ссылается псевдоним соединения сервера.  
  
## <a name="remarks"></a>Замечания  
  
