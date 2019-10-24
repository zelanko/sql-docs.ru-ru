---
title: Запуск Windows PowerShell из среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c6d71f1158ef73b84e5b04dcc9a1970bfd7dce35
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783095"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Запуск Windows PowerShell из среды SQL Server Management Studio
  Можно запускать сеансы Windows PowerShell из **обозревателя объектов** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] запускает Windows PowerShell, загружает `sqlps` модуль и задает контекст пути для связанного узла в дереве **обозревателя объектов** .  
  
## <a name="before-you-begin"></a>Перед началом  
 После указания того, что PowerShell необходимо вызвать на выполнение для некоторого объекта в **обозревателе объектов**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] начинает сеанс Windows PowerShell, в котором были загружены и зарегистрированы оснастки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. Путем для сеанса становится расположение объекта, выбранного правой кнопкой мыши в обозревателе объектов. Например, если щелкнуть правой кнопкой мыши объект базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] в обозревателе объектов, а затем выбрать команду **Запустить PowerShell**, то путь Windows PowerShell будет иметь следующий вид:  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a>Запуск PowerShell из среды SQL Server Management Studio 
  
1.  Откройте **обозреватель объектов**.  
  
2.  Перейдите к узлу для объекта, с которым выполняется работа.  
  
3.  Щелкните объект правой кнопкой мыши и выберите команду **Запустить PowerShell**.  
  
## <a name="permissions"></a>Permissions  
 При открытии из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]программа PowerShell не запускается с правами администратора, что может стать причиной того, что некоторые действия не будут выполнены, например вызовы инструментария WMI.  
  
## <a name="see-also"></a>См. также статью  
 [SQL Server PowerShell](sql-server-powershell.md)  
