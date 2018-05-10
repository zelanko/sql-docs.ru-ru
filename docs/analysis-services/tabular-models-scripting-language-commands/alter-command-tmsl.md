---
title: ALTER, команда (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9d0c1246c81438880145b0b90037726ef85caa2a
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="alter-command-tmsl"></a>Команда ALTER (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Изменяет существующий объект, но не его дочерние элементы, на экземпляре служб Analysis Services в табличном режиме.  Если объект не существует, команда вызывает ошибку.  
  
 Используйте **Alter** для целевых обновлений, например без указания всех столбцов, а также можно задать свойство в таблице. Эта команда аналогична **CreateOrReplace**, но без необходимости оставлять полное определение объекта.  
  
 Для объектов, имеющий свойства чтения и записи, если указать одно свойство для чтения и записи, необходимо указать все их с помощью нового или существующего значения. Объекты AMO PowerShell можно использовать для получения списка свойств. 
  
## <a name="request"></a>Запрос  
 **ALTER** не поддерживает какие-либо атрибуты. Входные данные включают объекта может быть изменен, за которым следует определение измененный объект.  
  
 Следующий пример иллюстрирует синтаксис для изменения свойства в объект секции. Путь к объекту устанавливает какой раздел должен быть изменены через пары имя значение родительских объектов. Второй набор входных данных является объект partition, указывающее новое значение свойства.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "\<database-name>",   
      "table": "\<table-name>",   
      "partition": "\<partition-name>"   
    },   
    "partition": {   
      "name": "\<new-partition-name>",   
       . . .  << other properties   
    }   
  }   
}   
```  
  
 Структура запроса различается в зависимости от объекта. **ALTER** может использоваться с любым из следующих объектов:  
  
 [Объект базы данных &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) переименование базы данных.  
  
```  
"alter": {   
    "object": {   
      "database": "\<database-name>"  
    },   
    "database": {   
      "name": "\<new-database-name>",   
    }   
  }   
```  
  
 [Источники данных объекта &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) переименовать соединение, которое является дочерним объектом базы данных.  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "dataSource":"SqlServer localhost AdventureworksDW2016"  
      },  
      "dataSource":{   
         "name":"A new connection name"  
      }  
   }  
}  
```  
  
 [Объект Tables &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) разделе **пример 1** ниже.  
  
 [Объект секции &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) разделе **пример 2** ниже.  
  
 [Объект роли &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) изменения свойства в объект role.  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "role":"DataReader"  
      },  
      "role":{   
         "name":"New Name"  
      }  
   }  
}  
```  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется сценарий, который можно выполнить в окно XMLA в среде Management Studio или использовать в качестве входных данных в [командлета Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) в AMO PowerShell.  
  
 **Пример 1** -этот скрипт изменяет свойство name в таблице.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "AdventureWorksDW2016",   
      "table": "DimDate"  
    },   
    "table": {   
      "name": "DimDate2"  
    }   
  }   
}  
```  
  
 При условии, что с локального именованного экземпляра (имя экземпляра является «таблицы») и JSON-файла с скрипт alter, эта команда изменяет имя таблицы с DimDate на DimDate2:  
  
 `invoke-ascmd -inputfile '\\my-computer\my-shared-folder\altertablename.json' -server 'localhost\Tabular'`  
  
 **Пример 2** --этот скрипт переименовывает секции, например в конце года, когда текущий год становится за предыдущий год. Не забудьте указать все свойства. Если оставить **источника** не указан, он может привести к нарушению все свои существующие определения секции.  
  
 Если вы создаете, заменив, или изменение сам объект источника данных, любой источник данных, на которые ссылается сценарий (например, приведенный ниже сценарий секционирования) должен быть существующим **DataSource** объектов в модели. Если необходимо изменить источник данных, сделайте это как отдельный шаг.  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "InternetSales",   
      "table": "DimDate",  
      "partition": "CurrentYear"  
    },   
    "partition": {   
      "name": "Year2009",  
       "source": {  
             "query":  "SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] WHERE [dbo].[DimDate].CalendarYear = 2009",  
              "dataSource": "SqlServer localhost AdventureworksDW2016"  
        }  
    }   
  }   
}  
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Не удается создать готовый сценарий для этой команды в среде SSMS. Вместо этого можно запустить с примером, или написать собственный.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40;TMSL&#41; ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  

## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
