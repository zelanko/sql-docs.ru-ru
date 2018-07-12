---
title: Свойство SqlServiceType (класс SqlServiceAdvancedProperty) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
caps.latest.revision: 42
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: affa3f0f79e0bba84e3400f019ad91b74faae8aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154145"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>Свойство SqlServiceType (класс SqlServiceAdvancedProperty)
  Возвращает тип управляемой службы, связанной с дополнительным свойством.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, задающее тип службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
