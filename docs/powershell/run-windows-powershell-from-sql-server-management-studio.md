---
title: Запуск Windows PowerShell из среды SQL Server Management Studio | Документация Майкрософт
description: Узнайте, как запустить сеанс Windows PowerShell из обозревателя объектов в SQL Server Management Studio с предустановленным путем к выбранному вами расположению объектов.
ms.prod: sql
ms.technology: sql-server-powershell
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: markingmyname
ms.author: maghan
ms.reviewer: matteot, drskwier
ms.custom: ''
ms.date: 03/14/2017
ms.openlocfilehash: c074b0f0ed5f5b041a8a4c4ed341837fec2b1926
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006165"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Запуск Windows PowerShell из среды SQL Server Management Studio

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Можно запускать сеансы Windows PowerShell из **обозревателя объектов** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] запускает Windows PowerShell, загружает модуль **SqlServer** и задает контекст пути для связанного узла в дереве **обозревателя объектов**.  

[!INCLUDE [sql-server-powershell-version](../includes/sql-server-powershell-version.md)]

После указания того, что PowerShell необходимо вызвать на выполнение для некоторого объекта в **обозревателе объектов**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] начинает сеанс Windows PowerShell, в котором были загружены и зарегистрированы оснастки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. Путем для сеанса становится расположение объекта, выбранного правой кнопкой мыши в обозревателе объектов. Например, если щелкнуть правой кнопкой мыши объект базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] в обозревателе объектов, а затем выбрать команду **Запустить PowerShell**, то путь Windows PowerShell будет иметь следующий вид:  

```powershell
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```

## <a name="run-powershell"></a>Запуск PowerShell

### <a name="to-run-powershell-from-sql-server-management-studio"></a>Запуск PowerShell из среды SQL Server Management Studio

1. Откройте **обозреватель объектов**.

2. Перейдите к узлу для объекта, с которым выполняется работа.

3. Щелкните объект правой кнопкой мыши и выберите команду **Запустить PowerShell**.

## <a name="permissions"></a>Разрешения

При открытии из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] программа PowerShell не запускается с правами администратора, что может стать причиной того, что некоторые действия не будут выполнены, например вызовы инструментария WMI.  
  
## <a name="see-also"></a>См. также:

- [SQL Server PowerShell](sql-server-powershell.md)