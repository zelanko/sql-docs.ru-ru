---
title: "Вызов ProcessASDatabase | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 66d5d154-88ce-4c2e-b1ef-e2d2f6fb1c44
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8e83493ed934a3f9bf32a1cef35969f04996223
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-processasdatabase"></a>Invoke-ProcessASDatabase

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Выполняет операцию **Process** для указанной базы данных **Database** с определенным типом **ProcessType** или **RefreshType** , в зависимости от базового типа метаданных.  
  
 Для баз данных с многомерными метаданными используйте **ProcessType** (сюда относятся табличные базы данных с уровнем совместимости 1050, 1100 и 1103).  
  
 Для табличных баз данных с уровнем совместимости 1200 или выше используйте **RefreshType** .  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-RefreshType] <RefreshType> {Full | ClearValues | Calculate |     DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-ProcessType] <ProcessType> {ProcessFull | ProcessAdd |     ProcessUpdate | ProcessIndexes | ProcessData | ProcessDefault | ProcessClear | ProcessStructure |     ProcessClearStructureOnly | ProcessScriptCache | ProcessRecalc | ProcessDefrag} [-Server <string>] [-Credential     <pscredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Командлет **Invoke-ProcessASDatabase** обрабатывает базу данных до указанного вами уровня. Например, для табличных баз данных с уровнем совместимости 1200 присвоение значения **Full** параметру **RefreshType** приведет к замене существующих данных на новые.  
  
 Тип обработки (многомерный) или тип обновления (табличный) является обязательным и указывается до или после параметров базы данных и сервера:  
  
-   Дополнительные сведения о многомерных базах данных см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
-   Дополнительные сведения о табличных базах данных см. в разделе [Обработка базы данных, таблицы или секции (службы Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-databasename-string"></a>Имя базы данных - \<строка >  
 Указывает тип обрабатываемой базы данных (табличная или многомерная).  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-servermicrosoftanalysissevicesserver"></a>-Сервер\<Microsoft.AnalysisSevices.Server >  
 Если для своего контекста вы не используете каталог поставщика **SQLAS** , дополнительно указывает экземпляр сервера, к которому нужно подключиться.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-refreshtype-microsoftanalysisservicesrefreshtype"></a>-RefreshType \<Microsoft.AnalysisServices.RefreshType >  
 Указывает тип обработки для табличной базы данных.  Допустимые значения: Full, ClearValues, Calculate, DataOnly, Automatic, Add и Defragment. Описания и инструкции см. в разделе [Обработка базы данных, таблицы или секции (службы Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>Тип процесса - \<Microsoft.AnalysisServices.ProcessType >  
 Указывает тип обработки для многомерной или табличной базы данных с уровнями совместимости 1050–1103. Допустимые значения: ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc и другие. Описания и инструкции см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-credential"></a>-Credential  
 Если этот параметр задан, указанные имя пользователя и пароль будут использоваться для подключения к экземпляру служб Analysis Services. Если учетные данные не будут указаны, будут использованы учетные данные по умолчанию для пользователя Windows, который запускает этот сценарий.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
## <a name="-whatif"></a>-Whatif  
 Укажите этот параметр, чтобы получить сведения о результатах операции до ее выполнения.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
## <a name="-confirm"></a>-Confirm  
 Укажите этот параметр, чтобы интерактивно подтвердить выполнение операции (диалоговое окно с кнопками "Да" и "Нет") до ее выполнения.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?||  
|Значение по умолчанию||  
|Принимать входные данные конвейера?||  
|Принимать символы-шаблоны?|false|  
  
## <a name="example-1-sqlas-provider"></a>Пример 1 (поставщик SQLAS)  
 В этом примере с помощью поставщика **SQLAS** задается контекст для списка баз данных в экземпляре по умолчанию.  Сформировав список содержимого каталога баз данных, вы увидите все базы данных вместе с их состоянием обработки и режимами чтения и записи.  
  
 Запустите командлет **Invoke ProcessASDatabase** , указав только имя базы данных.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server > cd sqlas\ssas-srv-01\default\databases  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> dir  
. . . .  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> Invoke-ProcessASDatabase "adventureworks"  
  
```  
  
 В зависимости от типа базы данных вам будет предложено выбрать параметр **RefreshType** или **ProcessType**.  
  
 О завершении обработки свидетельствует наличие объекта влияния в возвращаемом значении: Microsoft.AnalysisServices.Tabular.ObjectImpact.  
  
 Обратите внимание, что иногда сведения о состоянии объекта кэшируются, поэтому если вывести содержимое каталога после успешного завершения обработки, состояние базы данных сохранит исходный дескриптор "не обработано". Это вводит в заблуждение, так как фактически после возврата объекта ObjectImpact база данных является обработанной.  
  
 Чтобы убедиться в успешном завершении обработки, откройте страницу свойств базы данных в среде Management Studio, запустите новый сеанс или верните состояние обработки из объекта базы данных (через [Microsoft.AnalysisServices.ProcessableMajorObject.LastProcessed](https://msdn.microsoft.com/library/microsoft.analysisservices.processablemajorobject.lastprocessed.aspx)).  
  
## <a name="example-2"></a>Пример 2  
 В этом примере показана та же операция, но только с помощью командлета, без поставщика. Чтобы указать сервер и тип обработки, необходимы дополнительные параметры.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server >  Invoke-ProcessASDatabase -databasename "AdventureWorks" -server '\\server-name\instancename' –ProcessType "ProcessFull"  
  
```  
  
  
  

