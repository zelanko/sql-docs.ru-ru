---
title: "Справочник по компоненту Analysis Services PowerShell | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Справочник по компоненту Analysis Services PowerShell
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] включают поставщик PowerShell (SQLAS) и командлеты (SQLASCMDLETS), которые позволяют использовать Windows PowerShell для навигации, администрирования и выполнения запросов к объектам служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения о загрузке и использовании поставщика и командлетов см. в разделе [Создание скриптов PowerShell в службах Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md). Пример использования типов объектов AMO в PowerShell для создания табличной базы данных см. в разделе [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_cmdlets"></a> Командлеты служб Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет командлеты, соответствующие методам в пространстве имен **Microsoft.AnalysisServices**. Следующая таблица содержит описание каждого командлета и ссылки на соответствующие методы объектов AMO.  
  
 Если PowerShell используется для выполнения задачи, отсутствующей в следующем списке (например, создание или синхронизация базы данных), для соответствующего действия можно написать скрипт TMSL или XMLA и выполнить его с помощью командлета **Invoke-ASCmd**.  
  
|Командлет|Description|Эквивалентные методы AMO|  
|------------|-----------------|----------------------------|  
|[Командлет Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)|Добавление члена к роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Командлет Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Резервное копирование базы данных служб Analysis Services.|<xref:Microsoft.AnalysisServices.Database.Backup%2A>|  
|[Командлет Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|Выполнение запроса или сценария в формате XMLA или TSML (JSON).|<xref:Microsoft.AnalysisServices.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|Обработка базы данных.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|Обработка куба.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|Обработка измерения.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-PolicyEvaluation](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|Обработка секции.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|Обработка таблицы в табличной модели, модели совместимости 1200 или более поздней версии.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Командлет Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)|Слияние секций.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Командлет New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|Создайте папку, в которой будет содержаться резервная копия базы данных.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Командлет New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|Укажите один или несколько удаленных серверов, на которых будет восстановлена база данных.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Командлет Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|Удалите члена из роли базы данных.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Командлет Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|Восстановите базу данных на экземпляре сервера.|<xref:Microsoft.AnalysisServices.Server.Restore%2A>|  
  
## См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)  
  
  