---
title: "Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c439a76e3e925d00e88adaaefa616e59f8529a40
ms.lasthandoff: 04/11/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Вы можете отформатировать результаты запроса как JSON или экспортировать данные из SQL Server в формате JSON, добавив предложение **FOR JSON** к инструкции **SELECT**. Предложение **FOR JSON** позволяет делегировать форматирование выходных данных JSON из клиентских приложений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
 При использовании предложения **FOR JSON** можно явно указать структуру выходных данных или позволить определить выходные данные структуре инструкции SELECT.  
  
-   Используйте режим **PATH** с предложением **FOR JSON**, чтобы сохранить полный контроль над форматом выходных данных JSON. Вы можете создавать объекты-оболочки и вкладывать сложные свойства друг в друга.  
  
-   Для автоматического форматирования выходных данных JSON на основе структуры инструкции SELECT используйте режим **AUTO** с предложением **FOR JSON**.  
  
Ниже приведен пример инструкции **SELECT** с предложением **FOR JSON** и ее выходные данные.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## <a name="maintain-control-over-json-output-with-path-mode"></a>Управление выходными данными JSON в режиме PATH  
В режиме **PATH** можно использовать синтаксис с точкой — например, `'Item.Price'` — для форматирования вложенных выходных данных. В следующем примере также используется параметр **ROOT** для указания именованного корневого элемента.  

Ниже приведен пример запроса, где режим **PATH** с предложением **FOR JSON** .
  
 ![Диаграмма передачи выходных данных FOR JSON](../../relational-databases/json/media/forjson-example1.png "Диаграмма передачи выходных данных FOR JSON")  

### <a name="more-info"></a>Дополнительные сведения
Дополнительные сведения и примеры см. в разделе [Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="let-the-select-statement-control-json-output-with-auto-mode"></a>Разрешение инструкции SELECT управлять выходными данными JSON в режиме AUTO  
В режиме **AUTO** структура инструкции SELECT определяет формат выходных данных JSON. По умолчанию значения **NULL** не включаются в выходные данные. Это поведение можно изменить с помощью **INCLUDE_NULL_VALUES** .  

Ниже приведен пример запроса, где режим **AUTO** используется с предложением **FOR JSON** .
 
**Запрос:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Результаты**  
  
```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
### <a name="more-info"></a>Дополнительные сведения
Дополнительные сведения и примеры см. в разделе [Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Управление другими параметрами выходных данных JSON  
 Управлять выходными данными предложения **FOR JSON** можно с помощью следующих параметров.  
  
-   Чтобы добавить один элемент верхнего уровня в выходные данные JSON, укажите параметр **ROOT** . Если не указать параметр **ROOT** , выходные данные JSON не будут содержать корневой элемент. Дополнительные сведения см. в разделе [Добавление корневого узла в выходные данные JSON с параметром ROOT (SQL Server)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   Чтобы включить значения NULL в выходные данные JSON, укажите параметр **INCLUDE_NULL_VALUES** . Если не указать этот параметр, в выходные данные не будут включены свойства JSON для значений NULL в результатах запроса. Дополнительные сведения см. в разделе[Использование параметра INCLUDE_NULL_VALUES для включения значений Null в выходные данные JSON (SQL Server)](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   Чтобы удалить квадратные скобки, в которые выходные данные JSON предложения **FOR JSON** заключаются по умолчанию, укажите параметр **WITHOUT_ARRAY_WRAPPER** . Этот параметр позволяет создать единый объект JSON в качестве выходных данных. Если не указать этот параметр, выходные данные JSON будут заключены в квадратные скобки. Дополнительные сведения см. в разделе [Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Выходные данные предложения FOR JSON  
 Выходные данные предложения **FOR JSON** имеют следующие характеристики.  
  
1.  Результирующий набор содержит один столбец. Небольшой результирующий набор может содержать одну строку. Большой результирующий набор содержит несколько строк.  
  
     ![Пример выходных данных FOR JSON](../../relational-databases/json/media/forjson-example2.png "Пример выходных данных FOR JSON")  
  
2.  Результаты форматируются в виде массива объектов JSON.  
  
    -   Количество элементов в массиве равно количеству строк в результатах.  
  
    -   Каждая строка в результирующем наборе становится отдельным объектом JSON в массиве.  
  
    -   Каждый столбец в результирующем наборе становится свойством объекта JSON.  
  
3.  Как имена столбцов, так и их значения экранируются согласно синтаксису JSON. Дополнительные сведения см. в разделе [Как FOR JSON экранирует специальные и управляющие символы (SQL Server)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
 Ниже приведен пример, демонстрирующий форматирование выходных данных JSON.  
  
 **Результаты запроса**  
  
|||||  
|-|-|-|-|  
|**Объект**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|Да|  
|30|31|32|Z|  
  
 **Выходные данные JSON**  
  
```json  
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  
 Дополнительные сведения о том, какое содержимое отображается в выходных данных предложения **FOR JSON**, см. в следующих статьях.  
-   [Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
Предложение **FOR JSON** использует правила, описанные в этом разделе, для преобразования типов данных SQL в типы JSON в выходных данных JSON.  

-   [Как FOR JSON экранирует специальные и управляющие символы (SQL Server)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 Предложение **FOR JSON** экранирует специальные символы и представляет управляющие символы в выходных данных JSON, как описано в этом разделе.  

## <a name="learn-more-about-for-json-and-built-in-json-support-in-sql-server"></a>Дополнительные сведения о предложении FOR JSON и встроенной поддержке JSON в SQL Server  
 [Публикации блога Йована Поповича (Jovan Popovic), руководителя программы Microsoft](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Использование выходных данных FOR JSON в SQL Server и клиентских приложениях (SQL Server)](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

