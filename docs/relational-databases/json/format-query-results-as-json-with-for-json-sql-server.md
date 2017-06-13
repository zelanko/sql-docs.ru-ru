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
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 06095384c6f6ec876e0d103186b1269d19056987
ms.contentlocale: ru-ru
ms.lasthandoff: 06/09/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Вы можете отформатировать результаты запроса как JSON или экспортировать данные из SQL Server в формате JSON, добавив предложение **FOR JSON** к инструкции **SELECT**. Используйте **FOR JSON** предложений, чтобы упростить клиентских приложений, делегировать форматирование выходных данных JSON из клиентских приложений для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
 При использовании предложения **FOR JSON** можно явно указать структуру выходных данных или позволить определить выходные данные структуре инструкции SELECT.  
  
-   Используйте **FOR JSON PATH** чтобы сохранить полный контроль над форматом выходных данных JSON. Вы можете создавать объекты-оболочки и вкладывать сложные свойства друг в друга.  
  
-   Используйте **FOR JSON AUTO** для форматирования выходных данных автоматически JSON на основе структуры инструкции SELECT.  
  
Ниже приведен пример инструкции **SELECT** с предложением **FOR JSON** и ее выходные данные.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## <a name="maintain-control-over-json-output-with-for-json-path"></a>Контролировать выходных данных JSON в FOR JSON PATH
В режиме **PATH** можно использовать синтаксис с точкой — например, `'Item.Price'` — для форматирования вложенных выходных данных.  

Ниже приведен пример запроса, где режим **PATH** с предложением **FOR JSON** . В следующем примере также используется параметр **ROOT** для указания именованного корневого элемента. 
  
 ![Диаграмма передачи выходных данных FOR JSON](../../relational-databases/json/media/forjson-example1.png "Диаграмма передачи выходных данных FOR JSON")  

### <a name="more-info"></a>Дополнительные сведения
Более подробные сведения и примеры см. в разделе [форматирование вложенных выходных данных JSON с помощью режима PATH &#40; SQL Server &#41; ](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="let-the-select-statement-control-json-output-with-for-json-auto"></a>Могли управлять инструкции SELECT выходных данных JSON в FOR JSON AUTO
В режиме **AUTO** структура инструкции SELECT определяет формат выходных данных JSON. По умолчанию значения **NULL** не включаются в выходные данные. Это поведение можно изменить с помощью **INCLUDE_NULL_VALUES** .  

Ниже приведен пример запроса, где режим **AUTO** используется с предложением **FOR JSON** .
 
**Запрос:**  
  
```sql  
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
Более подробные сведения и примеры см. в разделе [формат JSON выходные данные автоматически с помощью режима AUTO &#40; SQL Server &#41; ](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Управление другими параметрами выходных данных JSON  
Управление выходными данными из **FOR JSON** предложения, используя следующие дополнительные параметры.  
  
-   **КОРНЕВОЙ**. Чтобы добавить один элемент верхнего уровня в выходные данные JSON, укажите параметр **ROOT** . Если не указать этот параметр, выходные данные JSON не поддерживает корневой элемент. Дополнительные сведения см. в разделе [Добавление корневого узла в выходные данные JSON с параметром ROOT (SQL Server)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   **INCLUDE_NULL_VALUES**. Чтобы включить значения NULL в выходные данные JSON, укажите параметр **INCLUDE_NULL_VALUES** . Если не указать этот параметр, выходные данные не будут включены свойства JSON для значений NULL в результатах запроса. Дополнительные сведения см. в разделе [включать значения Null в выходные данные JSON использование параметра INCLUDE_NULL_VALUES &#40; SQL Server &#41; ](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   **WITHOUT_ARRAY_WRAPPER**. Чтобы удалить квадратные скобки, в которые выходные данные JSON предложения **FOR JSON** заключаются по умолчанию, укажите параметр **WITHOUT_ARRAY_WRAPPER** . Используйте этот параметр, чтобы создать единый объект JSON в качестве выходных данных из одной строки результата. Если не указать этот параметр, выходные данные JSON форматируются как массив — то есть, заключены в квадратные скобки. Дополнительные сведения см. в разделе [Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Выходные данные предложения FOR JSON  
 Выходные данные предложения **FOR JSON** имеют следующие характеристики.  
  
1.  Результирующий набор содержит один столбец.
    -   Небольшой результирующий набор может содержать одну строку.
    -   Большой результирующий набор разбивает длинную строку JSON по нескольким строкам.
        -   По умолчанию SQL Server Management Studio (SSMS) объединяет результаты в одну строку, если выходной параметр не **результаты в таблицу**. В строке состояния SSMS отображается действительного числа строк.
        -   Другие клиентские приложения может потребоваться кода для объединения результатов длительное время, объединяя содержимое нескольких строк. Пример этого кода в приложении C# см. в разделе [использование для выходных данных JSON в клиентском приложении C#](https://docs.microsoft.com/en-us/sql/relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server#use-for-json-output-in-a-c-client-app).
  
     ![Пример выходных данных FOR JSON](../../relational-databases/json/media/forjson-example2.png "Пример выходных данных FOR JSON")  
  
2.  Результаты форматируются в виде массива объектов JSON.  
  
    -   Число элементов в массиве JSON равно числу строк в результатах инструкции SELECT (до применения предложения FOR JSON). 
  
    -   Каждая строка в результатах инструкции SELECT (до применения предложения FOR JSON) становится отдельным объектом JSON в массиве.  
  
    -   Каждый столбец в результатах инструкции SELECT (до применения предложения FOR JSON) становится свойством объекта JSON.  
  
3.  Как имена столбцов, так и их значения экранируются согласно синтаксису JSON. Дополнительные сведения см. в разделе [Как FOR JSON экранирует специальные и управляющие символы (SQL Server)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
### <a name="example"></a>Пример
Ниже приведен пример, демонстрирующий использование **FOR JSON** предложение форматы выходных данных JSON.  
  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений варианты использования и рекомендации, см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базы данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).
  
## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Использование выходных данных FOR JSON в SQL Server и клиентских приложениях (SQL Server)](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

