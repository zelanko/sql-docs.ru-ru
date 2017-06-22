---
title: "Устранение распространенных проблем с JSON в SQL Server | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, FAQ
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 94435e9fb466887a00c8d22076f229481a83f280
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="solve-common-issues-with-json-in-sql-server"></a>Устранение распространенных проблем с JSON в SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Здесь приведены ответы на некоторые распространенные вопросы о встроенной поддержке JSON в SQL Server.  
 
## <a name="for-json-and-json-output"></a>Выходные данные FOR JSON и JSON

### <a name="for-json-path-or-for-json-auto"></a>FOR JSON PATH или FOR JSON AUTO?  
 **Вопрос.** Я хочу создать текстовый результат JSON из простого SQL-запроса для одной таблицы. Выходные данные для FOR JSON PATH и FOR JSON AUTO совпадают. Какой из этих вариантов следует использовать?  
  
 **Ответ.** Используйте FOR JSON PATH. Несмотря на то, что нет никаких различий в выходных данных JSON, режим AUTO применяет дополнительную логику, определяющую вложенных столбцов. Рассматривайте PATH как параметр по умолчанию.  

### <a name="create-a-nested-json-structure"></a>Создание вложенной структуры JSON  
 **Вопрос.** Я хочу создать сложную JSON с несколькими массивами на одном уровне. FOR JSON PATH может создавать вложенные объекты с использованием путей, а FOR JSON AUTO создает дополнительный уровень вложенности для каждой таблицы. Ни один из этих параметров позволяет получить результат, требуется. Как создать настраиваемый формат JSON, который напрямую не поддерживается существующими параметрами?  
  
 **Ответ.** Можно создать любую структуру данных, добавив запросы FOR JSON в качестве выражений столбца, возвращающих текст JSON. Можно также создать JSON вручную с помощью функции JSON_QUERY. В следующем примере показано следующее.  
  
```sql  
SELECT col1, col2, col3,  
     (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
     (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
     (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
     JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
Каждый результат запроса FOR JSON или функции JSON_QUERY в выражениях столбца форматируется в виде отдельного вложенного подчиненного объекта JSON и включается в основной результат.  

### <a name="prevent-double-escaped-json-in-for-json-output"></a>Предотвращение появления дважды экранированного JSON в выходных данных FOR JSON  
 **Вопрос.** Имеется текст JSON, хранящийся в столбце таблицы. Я хочу включить его в выходные данные FOR JSON. Но FOR JSON экранирует все символы в JSON, поэтому я получаю строку JSON вместо вложенного объекта, как показано в следующем примере.  
  
```sql  
SELECT 'Text' AS myText, '{"day":23}' AS myJson  
FOR JSON PATH  
```  
  
 Этот запрос получает следующие выходные данные.  
  
```json  
[{"myText":"Text", "myJson":"{\"day\":23}"}]  
```  
  
 Как можно избежать этого? Я хочу, чтобы `{"day":23}` возвращался в виде объекта JSON, а не escape-текста.  
  
 **Ответ.** JSON, хранящийся в столбце текста или литерале, обрабатывается как обычный текст. То есть он заключен в двойные кавычки и экранируется. Если требуется возвратить неэкранированный объект JSON, передайте столбца JSON в качестве аргумента в функцию JSON_QUERY, как показано в следующем примере.  
  
```sql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 JSON_QUERY без второго необязательного параметра возвращает в качестве результата только первый аргумент. Так как всегда JSON_QUERY возвращает правильную JSON, FOR JSON определяет, что этот результат не нуждается в экранировании.

### <a name="json-generated-with-the-withoutarraywrapper-clause-is-escaped-in-for-json-output"></a>JSON, созданная с помощью предложения WITHOUT_ARRAY_WRAPPER, экранируется в выходных данных FOR JSON  
 **Вопрос.** Я пытаюсь отформатировать выражение столбца с помощью FOR JSON и параметра WITHOUT_ARRAY_WRAPPER.  
  
```sql  
SELECT 'Text' as myText,  
   (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 Похоже, что текст, возвращаемый запросом FOR JSON, экранируется как обычный текст. Это происходит только в том случае, если указан WITHOUT_ARRAY_WRAPPER. Почему он не рассматривается в качестве объекта JSON и не включается в результат неэкранированным?  
  
 **Ответ.** При указании `WITHOUT_ARRAY_WRAPPER` параметр во внутреннем `FOR JSON`, полученный текст JSON не обязательно допустимых данных JSON. Поэтому внешний `FOR JSON` предполагается, что это обычный текст и экранирует строку. Если вы уверены, что выходные данные JSON, допустим, заключите их в оболочку с `JSON_QUERY` функции, чтобы превратить в правильно в формате JSON, как показано в следующем примере.  
  
```sql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## <a name="openjson-and-json-input"></a>Входные данные OPENJSON и JSON

### <a name="return-a-nested-json-sub-object-from-json-text-with-openjson"></a>Возвращение вложенного подчиненного объекта JSON из текста JSON с помощью OPENJSON  
 **Вопрос.** Не удается открыть массив сложных объектов JSON, содержащий скалярные значения, объекты и массивы, с помощью OPENJSON с явной схемой. Когда я ссылаюсь на ключ в предложении WITH, возвращаются только скалярные значения. Объекты и массивы возвращаются в виде значений NULL. Как извлечь объекты или массивы в объектах JSON?  
  
 **Ответ.** Если вам требуется возвратить объект или массив в виде столбца, используйте параметр AS JSON в определении столбца, как показано в следующем примере.  
  
```sql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
    WITH ( scalar1 int,  
        scalar2 datetime2,  
        obj1 NVARCHAR(MAX) AS JSON,  
        obj2 NVARCHAR(MAX) AS JSON,  
        arr1 NVARCHAR(MAX) AS JSON)  
```  

### <a name="return-long-text-value-with-openjson-instead-of-jsonvalue"></a>Возвращаемое значение длинный текст с помощью OPENJSON вместо JSON_VALUE
 **Вопрос.** В тексте JSON имеется ключ описания, содержащий длинный текст. `JSON_VALUE(@json, '$.description')` возвращает NULL, а не значение.  
  
 **Ответ.** JSON_VALUE предназначена для возврата небольших скалярных значений. Обычно эта функция возвращает значение NULL вместо ошибки переполнения. Если требуется возвратить более длинные значения, используйте OPENJSON, поддерживающую значения NVARCHAR(MAX), как показано в следующем примере.  
  
```sql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### <a name="handle-duplicate-keys-with-openjson-instead-of-jsonvalue"></a>Обработка повторяющихся ключей с помощью OPENJSON вместо JSON_VALUE
 **Вопрос.** В тексте JSON есть повторяющиеся ключи. JSON_VALUE возвращает только первый ключ, найденный в пути. Как возвратить все ключи с одинаковыми именами?  
  
 **Ответ.** Встроенные скалярные функции JSON возвращают только первое вхождение объекта, на который указывает ссылка. Если требуется получить несколько ключей, используйте функцию с табличным значением OPENJSON, как показано в следующем примере.  
  
```sql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### <a name="openjson-requires-compatibility-level-130"></a>OPENJSON необходим уровень совместимости 130  
 **Вопрос.** Я пытаюсь выполнить OPENJSON в SQL Server 2016, но получаю следующую ошибку.  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **Ответ.** Функция OPENJSON доступна только при уровне совместимости 130. Если уровень совместимости базы данных ниже 130, функция OPENJSON будет скрыта. Другие функции JSON доступны на всех уровнях совместимости.  
 
## <a name="other-questions"></a>Другие вопросы

### <a name="reference-keys-that-contain-non-alphanumeric-characters-in-json-text"></a>Ключи ссылки, содержащие символы, отличные от буквенно-цифровых, в тексте JSON  
 **Вопрос.** Ключи в тексте JSON содержат символы, отличные от буквенно-цифровых. Как можно сослаться на эти свойства?  
  
 **Ответ.** Необходимо заключить их в кавычки в путях JSON. Например, `JSON_VALUE(@json, '$."$info"."First Name".value')`.
 
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений варианты использования и рекомендации, см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базы данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).

