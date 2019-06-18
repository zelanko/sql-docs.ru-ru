---
title: Запуск Windows PowerShell из среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 564bee6ec776b473503e98234fc543cdb5c0e5f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672407"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Запуск Windows PowerShell из среды SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Можно запускать сеансы Windows PowerShell из **обозревателя объектов** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] запускает Windows PowerShell, загружает модуль **SqlServer** и задает контекст пути для связанного узла в дереве **обозревателя объектов**.  
  

> [!NOTE]
> Существует два модуля SQL Server PowerShell — **SqlServer** и **SQLPS**. Модуль **SQLPS** входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**. Модуль **SqlServer** содержит обновленные версии командлетов в **SQLPS**, а также новые командлеты для поддержки последних функций SQL.  
> Предыдущие версии модуля **SqlServer** *входили* в состав среды SQL Server Management Studio (SSMS), но только с SSMS версий 16.x. Для работы PowerShell с SSMS 17.0 и более поздних версий необходимо установить модуль **SqlServer** из коллекции PowerShell.
> Сведения об установке модуля **SqlServer** см. в статье [Установка компонентов SQL Server PowerShell](download-sql-server-ps-module.md).



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
 При открытии из среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] программа PowerShell не запускается с правами администратора, что может стать причиной того, что некоторые действия не будут выполнены, например вызовы инструментария WMI.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
