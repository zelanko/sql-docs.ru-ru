---
title: "Командлет Invoke-ProcessTable | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 865e6d06-b99a-41f3-9d6f-c3c97b529b23
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e2a7f1392931ec5edd41803f6df6d98aa95403dd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="invoke-processtable-cmdlet"></a>Командлет Invoke-ProcessTable
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Проводит **процесс** операции **таблицы** с определенным **RefreshType**.  

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
  
  
