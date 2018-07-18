---
title: Службы Analysis Services PowerShell Reference | Документация Майкрософт
ms.date: 06/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13ea15a23bbf6de6c50b494f709f65cae2f7c48b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992906"
---
# <a name="analysis-services-powershell-reference"></a>Справочник по компоненту Analysis Services PowerShell
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Командлеты PowerShell включены в [модуля SqlServer](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
>[!NOTE] 
> Azure операций базы данных Analysis Services используется один и тот же модуль SqlServer как SQL Server Analysis Services. Тем не менее для служб Azure Analysis Services поддерживаются не все командлеты. Дополнительные сведения см. в разделе [управление Azure Analysis Services с помощью PowerShell](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell).
  
##  <a name="bkmk_cmdlets"></a> Командлеты служб Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет командлеты, соответствующие методам в пространстве имен **Microsoft.AnalysisServices** . Следующая таблица содержит описание каждого командлета и ссылки на соответствующие методы объектов AMO.  
  
 Если PowerShell используется для выполнения задачи, отсутствующей в следующем списке (например, создание или синхронизация базы данных), для соответствующего действия можно написать скрипт TMSL или XMLA и выполнить его с помощью командлета **Invoke-ASCmd** .  
  
|Командлет|Описание|Эквивалентные методы AMO|  
|------------|-----------------|----------------------------|  
|[Командлет Add-RoleMember](https://docs.microsoft.com/powershell/module/sqlserver/Add-RoleMember)|Добавление члена к роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Командлет Backup-ASDatabase](https://docs.microsoft.com/powershell/module/sqlserver/backup-asdatabase)|Резервное копирование базы данных служб Analysis Services.|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Командлет Invoke-ASCmd](https://docs.microsoft.com/powershell/module/sqlserver/invoke-ascmd)|Выполнение запроса или сценария в формате XMLA или TSML (JSON).|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processasdatabase)|Обработка базы данных.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessCube](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processcube)|Обработка куба.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessDimension](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processdimension)|Обработка измерения.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessPartition](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processpartition)|Обработка секции.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessTable](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processtable)|Обработка таблицы в табличной модели, модели совместимости 1200 или выше.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Merge-Partition](https://docs.microsoft.com/powershell/module/sqlserver/merge-partition)|Слияние секций.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Командлет New-RestoreFolder](https://docs.microsoft.com/powershell/module/sqlserver/new-restorefolder)|Создайте папку, в которой будет содержаться резервная копия базы данных.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Командлет New-RestoreLocation](https://docs.microsoft.com/powershell/module/sqlserver/new-restorelocation)|Укажите один или несколько удаленных серверов, на которых будет восстановлена база данных.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Командлет Remove-RoleMember](https://docs.microsoft.com/powershell/module/sqlserver/remove-rolemember)|Удалите члена из роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Командлет Restore-ASDatabase](https://docs.microsoft.com/powershell/module/sqlserver/restore-asdatabase)|Восстановите базу данных на экземпляре сервера.|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
