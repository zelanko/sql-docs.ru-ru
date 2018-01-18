---
title: "Справочник по PowerShell | Документы Microsoft"
ms.custom: 
ms.date: 06/21/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9fbe93dba70125f12d20ee6ae2227d477b08ef19
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="analysis-services-powershell-reference"></a>Справочник по компоненту Analysis Services PowerShell
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Командлеты PowerShell включены в [модуля SqlServer](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
>[!NOTE] 
> Azure операций базы данных служб Analysis Services используется один и тот же модуль SqlServer как SQL Server Analysis Services. Однако для служб Azure Analysis Services поддерживаются не все командлеты. Дополнительные сведения см. в разделе [управление Azure Analysis Services с помощью PowerShell](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell).
  
##  <a name="bkmk_cmdlets"></a> Командлеты служб Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет командлеты, соответствующие методам в пространстве имен **Microsoft.AnalysisServices** . Следующая таблица содержит описание каждого командлета и ссылки на соответствующие методы объектов AMO.  
  
 Если PowerShell используется для выполнения задачи, отсутствующей в следующем списке (например, создание или синхронизация базы данных), для соответствующего действия можно написать скрипт TMSL или XMLA и выполнить его с помощью командлета **Invoke-ASCmd** .  
  
|Командлет|Описание|Эквивалентные методы AMO|  
|------------|-----------------|----------------------------|  
|[Командлет Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)|Добавление члена к роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Командлет Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Резервное копирование базы данных служб Analysis Services.|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Командлет Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|Выполнение запроса или сценария в формате XMLA или TSML (JSON).|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|Обработка базы данных.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|Обработка куба.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|Обработка измерения.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-PolicyEvaluation](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|Обработка секции.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|Обработка таблицы в табличной модели, модели совместимости 1200 или выше.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)|Слияние секций.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Командлет New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|Создайте папку, в которой будет содержаться резервная копия базы данных.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Командлет New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|Укажите один или несколько удаленных серверов, на которых будет восстановлена база данных.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Командлет Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|Удалите члена из роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Командлет Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|Восстановите базу данных на экземпляре сервера.|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
