---
title: "Создание команды (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e3024f89-ebfa-47e4-9893-708f379fd9b8
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae07d8b17fc659bb8a8bc2bef1cdcb6421606c29
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-command-tmsl"></a>Создание команды (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Создает указанный объект и все дочерние объекты, которые указаны. Если объект уже существует, команда вызывает ошибку.  
  
## <a name="request"></a>Запрос  
 Структура запроса различается в зависимости от объекта. Объект, который является родительским должна включать все его дочерние элементы, несмотря на то, что полный объект определения одноуровневые элементы и родительские элементы не являются обязательными.  
  
 [Объект базы данных &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) Добавить базу данных на сервере.  
  
```  
{   
  "create": {   
    "database": {   
      "name": "AdventureworksDW2016",   
      "description": "<description>",   
      "tables": [   
        { },   
        { },   
        { }   
      ],   
      "relationships": [   
        { },   
        { }   
      ]   
    }   
  }   
}  
```  
  
 [Объект источника данных &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureworksDW2016"  
    },  
    "dataSource": {  
      "name": "SqlServer localhost AdventureworksDW2016",  
      "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
      "impersonationMode": "impersonateAccount",  
      "account": "<account name>",  
      "annotations": [  
        {  
          "name": "ConnectionEditUISource",  
          "value": "SqlServer"  
        }  
      ]  
    }  
  }  
}  
```  
  
 [Объект Tables &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Добавление столбцов в таблицу.  
  
```  
{   
  "create": {   
    "parentObject": {   
      "database": "AdventureworksDW2016",   
      "table": "DimSales"  
    },   
    "columns": {   
      "type": ["calculated"  | "data" ]  
      "name": "\<column-name>",   
       "expression":  "<DAX expression>"  
    }   
  }   
}   
```  
  
 [Объект секций &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) Добавить секцию таблицы на родительский объект.  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureWorksTabular1200",  
      "table": "Date"  
    },  
    "partition": {  
      "name": "Date 2",  
      "source": {  
        "query": "SELECT [dbo].[DimDate].* FROM [dbo].[DimDate]",  
        "dataSource": "SqlServer localhost AdventureworksDW2016"  
      }  
    }  
  }  
}  
```  
  
 [Объект роли &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) Минимально добавить роль в базе данных, но без членство или фильтры.  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureWorksDW2016"  
    },  
    "role": {  
      "name": "DataReader",  
      "modelPermission": "read"  
    }  
  }  
}  
```  
  
 За исключением **базы данных** объекта, создаваемый объект является потомком указанного **parentObject**. Родительский **базы данных** объект всегда является **сервера** объекта.  
  
 Предполагается, что сервер из контекста. Например если запустить скрипт из среды Management Studio или AMO PowerShell, соединение с сервером указывается во время сеанса или в качестве параметра.  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="examples"></a>Примеры  
 **Пример 1** -добавить роль, которая определяет членство и фильтр.  
  
```  
{   
   "create":{   
      "parentObject":{   
         "database":"AdventureWorksTabular1200"  
      },  
      "role":{  
         "name":"DataReader",  
         "modelPermission":"read",  
         "members":[   
            {  
               "memberName": "account-01",  
               "memberId":"S-1-5-21-1111111111-2222222222-33333333-444444"  
            },  
            {   
               "memberName": "account-02",  
               "memberId":"S-2-5-21-1111111111-2222222222-33333333-444444"  
            }  
         ],  
         "tablePermissions":[   
            {   
               "name":"Date",  
               "filterExpression":"CalendarYear('2011')"  
            }  
         ]  
      }  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS.  Например, можно щелкнуть правой кнопкой мыши существующую базу данных > **сценарий** > **скрипта базы данных в качестве** > **создать в**.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40; TMSL &#41; Ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  

## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
