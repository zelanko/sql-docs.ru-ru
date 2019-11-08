---
title: Свойство SqlServiceType (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db0a9b0d2461e392f981ba3699a9efd3c1f3f8f3
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73660875"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>Свойство SqlServiceType (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает тип управляемой службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, задающее тип службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="remarks"></a>Замечания  
 Может возвращаться одно из следующих значений:  
  
|Тип|Определение|  
|----------|----------------|  
|*1*|MSSQLSERVER — служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , агент».|  
|*3*|MSFTESQL — служба средства полнотекстового поиска [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*4*|MsDtsServer — служба [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5*|MSSQLServerOLAPService — служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer — служба [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обозреватель».|  
|*8*|Нссервице — служба уведомлений [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)].|  
|*8*|MSSQLFDLauncher — это служба запуска управляющей программы полнотекстовой фильтрации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*10*|СКЛПБЕНГИНЕ — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба ядра polybase.|  
|*11*|СКЛПБДМС — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба перемещения данных polybase.|  
|*12*|MSSQLLaunchpad — это служба панели запуска [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также раздел  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
