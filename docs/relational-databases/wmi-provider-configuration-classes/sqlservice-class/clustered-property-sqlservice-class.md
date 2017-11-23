---
title: "Кластерные свойство (класс SqlService) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Clustered Property (SqlService Class)
apilocation: sqlmgmproviderxpsp2up.mof
helpviewer_keywords: Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5f86c229aa422a01f02af4f94fbff5526fb27a04
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="clustered-property-sqlservice-class"></a>Свойство Clustered (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Возвращает логическое значение, указывающее, является ли служба частью кластеризованного экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Clustered [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, определяющее, участвует ли служба в кластеризованном экземпляре: **true** , если участвует; в противном случае — **false** .  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
