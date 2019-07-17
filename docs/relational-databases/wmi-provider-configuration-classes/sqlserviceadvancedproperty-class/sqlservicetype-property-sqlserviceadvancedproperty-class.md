---
title: Свойство SqlServiceType (класс SqlServiceAdvancedProperty) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30b69a61f184738f72fce32920d8aeedd62797eb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139463"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>Свойство SqlServiceType (класс SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает тип управляемой службы, связанной с дополнительным свойством.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, задающее тип службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Примечания  
 Может возвращаться одно из следующих значений:  
  
|Type|Определение|  
|----------|----------------|  
|*1*|MSSQLSERVER — служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , агент».|  
|*3*|MSFTESQL — служба средства полнотекстового поиска [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*4*|MsDtsServer — служба [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5*|MSSQLServerOLAPService — служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer — служба [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обозреватель».|  
|*8*|— NsService [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] службу уведомлений.|  
|*9*|— MSSQLFDLauncher [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] службы запуска управляющей программы фильтрации для полнотекстового поиска.|  
|*10*|— SQLPBENGINE [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] службы Polybase Engine.|  
|*11*|— SQLPBDMS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] службе перемещения данных Polybase.|  
|*12*|— MSSQLLaunchpad [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба панели запуска.|  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
