---
title: Командлет Invoke-ProcessTable | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8fde6817c48df9aa5c3e663a5b76223be84f1a69
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="invoke-processtable-cmdlet"></a>Командлет Invoke-ProcessTable
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Выполняет операцию **Обработка** в **таблице** с определенным типом **RefreshType**.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `Invoke-ProcessTable [-DatabaseName] <string> [-TableName] <string> [-RefreshType] <RefreshType> {Full |     ClearValues | Calculate | DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>     [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
 `Invoke-ProcessTable -RefreshType <RefreshType> {Full | ClearValues | Calculate | DataOnly | Automatic | Add |     Defragment} -Table <Table> [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-tablename-string"></a>-TableName \<строка >  
 Имя таблицы, к которой принадлежит подлежащая обработке секция.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-databasename-string"></a>Имя базы данных - \<строка >  
 Указывает базу данных, к которой относится таблица.  
  
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
  
### <a name="-credential"></a>-Credential  
 Если этот параметр задан, указанные имя пользователя и пароль будут использоваться для подключения к экземпляру служб Analysis Services. Если учетные данные не будут указаны, будут использованы учетные данные по умолчанию для пользователя Windows, который запускает этот сценарий.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-whatif"></a>-Whatif  
 Укажите этот параметр, чтобы получить сведения о результатах операции до ее выполнения.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-confirm"></a>-Confirm  
 Укажите этот параметр, чтобы интерактивно подтвердить выполнение операции (диалоговое окно с кнопками "Да" и "Нет") до ее выполнения.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?||  
|Значение по умолчанию||  
|Принимать входные данные конвейера?||  
|Принимать символы-шаблоны?|false|  
  
## <a name="example-1"></a>Пример 1  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType "Full"`  
  
 Эта команда передает в конвейер удостоверение обрабатываемой таблицы.  
  
## <a name="example-2"></a>Пример 2  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType [Microsoft.AnalysisServices.Tabular.RefreshType]::Full`  
  
 Эта команда обрабатывает таблицу с табличными метаданными с использованием типа обновления **enum** .  
  
  
