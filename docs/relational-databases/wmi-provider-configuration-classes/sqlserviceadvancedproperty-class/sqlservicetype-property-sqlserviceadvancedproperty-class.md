---
title: Свойство SqlServiceType (класс sqlserviceadvancedproperty)
ms.custom: seo-lt-2019
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
ms.openlocfilehash: 59c42bdb98d5ed19ea2d415a85e9d2ccb4aeb8b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73658959"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>Свойство SqlServiceType (класс SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает тип управляемой службы, связанной с дополнительным свойством.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, задающее тип службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Remarks  
 Может возвращаться одно из следующих значений:  
  
|Тип|Определение|  
|----------|----------------|  
|*1*|MSSQLSERVER — служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , агент».|  
|*3-5*|MSFTESQL — служба средства полнотекстового поиска [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*4*|MsDtsServer — служба [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5.0*|MSSQLServerOLAPService — служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer — служба [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser — служба « [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обозреватель».|  
|*8*|Нссервице — это [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] служба уведомлений.|  
|*8*|MSSQLFDLauncher — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба запуска управляющей программы полнотекстовой фильтрации.|  
|*штук*|СКЛПБЕНГИНЕ — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба ядра polybase.|  
|*11*|СКЛПБДМС — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба перемещения данных polybase.|  
|*12*|MSSQLLaunchpad — это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба панели запуска.|  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
