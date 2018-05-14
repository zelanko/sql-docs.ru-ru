---
title: Справочник по PowerShell | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9632b9aaecfc6f6fa86684ac604706ecaac90071
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-powershell-reference"></a>Справочник по компоненту Analysis Services PowerShell
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Командлеты PowerShell включены в [модуля SqlServer](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
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
  

  
  
