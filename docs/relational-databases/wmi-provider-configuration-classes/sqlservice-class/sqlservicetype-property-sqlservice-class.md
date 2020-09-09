---
description: Свойство SqlServiceType (класс SqlService)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 685fb402647c7a757f7a894705cf7754d696b24d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542820"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>Свойство SqlServiceType (класс SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
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
  
## <a name="remarks"></a>Примечания  
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
|*8*|Нссервице — это [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Служба уведомлений.|  
|*9*|MSSQLFDLauncher — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Служба запуска управляющей программы полнотекстовой фильтрации.|  
|*10*|СКЛПБЕНГИНЕ — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Служба ядра polybase.|  
|*11*|СКЛПБДМС — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Служба перемещения данных polybase.|  
|*12*|MSSQLLaunchpad — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба панели запуска.|  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
