---
title: Импорт данных с помощью собственного запроса (службы Analysis Services) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 67466abfccb03a689d5f717159e833143fcfafb4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472060"
---
# <a name="import-data-by-using-a-native-query"></a>Импорт данных с помощью машинного запроса
[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]
Для табличных моделей 1400 новый интерфейс получения данных в проектах Visual Studio Analysis Services обеспечивает огромную гибкость при способы комбинирования данных во время импорта. В этой статье описывается создание подключения к источнику данных, а затем создать собственный запрос SQL для задания импорта данных.

Для выполнения задач, описанных в этой статье, убедитесь, что вы используете последнюю версию SSDT. Если вы используете Visual Studio 2017, убедитесь, что вы загрузили и установили сентября 2017 или более поздней версии Microsoft Analysis Services проекты VSIX.

[Скачать и установить SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Загрузите проекты служб Microsoft Analysis Services VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Создание подключения к источнику данных
Если у вас нет подключения к источнику данных, необходимо создать его.

1. В Visual Studio > **обозреватель табличных моделей**, щелкните правой кнопкой мыши **источников данных**, а затем нажмите кнопку **новый источник данных**.
2. В **получить данные**, выберите тип источника данных и нажмите кнопку **Connect**. Выполните какие дополнительные шаги, необходимые для подключения к источнику данных.


## <a name="enter-a-query-as-a-named-expression"></a>Введите запрос как именованное выражение
1. В **обозреватель табличных моделей**, щелкните правой кнопкой мыши **выражения** > **изменить выражения**.
2. В **редактора запросов**, нажмите кнопку **запроса** > **новый запрос** > **пустое окно запроса**
3. В строке формул введите
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM ...")
    ```
4. Чтобы создать таблицу, в **запросы**, щелкните правой кнопкой мыши запрос и затем выберите **создать таблицу**. Новая таблица будет иметь то же имя, что запрос.


## <a name="example"></a>Пример
Этот собственный запрос создает таблицу Employee в модели, которая включает в себя все столбцы из таблицы Dimension.Employee в источнике данных.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Редактор запросов](media/ssas-import-query-example.png)


После импорта, в модели создается таблицу Employees.   

![Редактор запросов](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>См. также  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Олицетворение](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
