---
title: "Импорт данных с помощью собственного запроса (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 10/26/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 8888951d9fca0013015105998200b3ee9364855d
ms.contentlocale: ru-ru
ms.lasthandoff: 10/11/2017

---
# <a name="import-data-by-using-a-native-query"></a>Импорт данных при помощи собственного запроса

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Для табличных моделей 1400 новые возможности получения данных в проектах Visual Studio Analysis Services обеспечивает огромную гибкость в том, как можно объединять данные во время импорта. Эта статья описывает создание подключения к источнику данных и последующего создания собственного SQL-запрос для задания импорта данных.

Для выполнения задач, описанных в этой статье, убедитесь, что вы используете последнюю версию SSDT. Если вы используете Visual Studio 2017 г., убедитесь, что вы загрузили и установили сентября 2017 г. или более поздней версии Microsoft Analysis Services проекты VSIX.

[Загрузите и установите SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Загрузить проекты служб Microsoft Analysis Services VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Создание подключения источника данных
Если у вас нет подключения к источнику данных, необходимо создать его.

1. В Visual Studio > **обозреватель табличной модели**, щелкните правой кнопкой мыши **источники данных**, а затем нажмите кнопку **новый источник данных**.
2. В **получить данные**, выберите тип источника данных и нажмите кнопку **Connect**. Выполните какие дополнительные шаги, необходимые для подключения к источнику данных.


## <a name="enter-a-query-as-a-named-expression"></a>Введите запрос в качестве именованного выражения
1. В **обозреватель табличной модели**, щелкните правой кнопкой мыши **выражений** > **редактирование выражений**.
2. В **редактора запросов**, нажмите кнопку **запроса** > **новый запрос** > **пустое окно запроса**
3. В строке формул введите
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM …")
    ```
4. Чтобы создать таблицу, в **запросы**, щелкните правой кнопкой мыши запрос и выберите **создать таблицу**. Новая таблица будет иметь имя, совпадающее с именем запроса.


## <a name="example"></a>Пример
Этот собственный запрос создает таблицу Employee в модель, включающую все столбцы из таблицы Dimension.Employee в источнике данных.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Редактор запросов](media/ssas-import-query-example.png)


После импорта, в модели создается таблицу Employees.   

![Редактор запросов](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>См. также:  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Олицетворение](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  

