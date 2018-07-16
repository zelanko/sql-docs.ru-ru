---
title: Запуск Windows PowerShell из среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f8ce7eb6e1ba660a676aa08087e689d1d6b1c550
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215154"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Запуск Windows PowerShell из среды SQL Server Management Studio
  Можно запускать сеансы Windows PowerShell из **обозревателя объектов** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] запускает Windows PowerShell, загружает `sqlps` модуля и задает контекст пути для связанного узла в **обозревателя объектов** дерева.  
  
## <a name="before-you-begin"></a>Перед началом  
 После указания того, что PowerShell необходимо вызвать на выполнение для некоторого объекта в **обозревателе объектов**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] начинает сеанс Windows PowerShell, в котором были загружены и зарегистрированы оснастки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. Путем для сеанса становится расположение объекта, выбранного правой кнопкой мыши в обозревателе объектов. Например, если щелкнуть правой кнопкой мыши объект базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] в обозревателе объектов, а затем выбрать команду **Запустить PowerShell**, то путь Windows PowerShell будет иметь следующий вид:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>Запуск PowerShell  
 **Запуск PowerShell из среды SQL Server Management Studio**  
  
1.  Откройте **обозреватель объектов**.  
  
2.  Перейдите к узлу для объекта, с которым выполняется работа.  
  
3.  Щелкните объект правой кнопкой мыши и выберите команду **Запустить PowerShell**.  
  
## <a name="permissions"></a>Разрешения  
 При открытии из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]программа PowerShell не запускается с правами администратора, что может стать причиной того, что некоторые действия не будут выполнены, например вызовы инструментария WMI.  
  
## <a name="see-also"></a>См. также  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
