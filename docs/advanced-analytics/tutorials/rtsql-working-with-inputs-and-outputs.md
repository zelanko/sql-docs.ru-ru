---
title: Краткое руководство по работе с входных и выходных данных в R (машинного обучения SQL Server) | Документация Майкрософт
description: В этом кратком руководстве для скрипта R в SQL Server Узнайте, как структурировать входных и выходных данных для системной хранимой процедуры sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b41a8c30cd0ecbe040819478c0cadece1b9eb704
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086586"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Краткое руководство: Обработка входных и выходных данных с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Если вы хотите запустить код R в SQL Server, нужно упаковать скрипт R в хранимой процедуре. Можно написать, или передать R-скрипте [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Эта система, хранимая процедура используется для запуска среды выполнения R в контексте SQL Server, который передает данные в R, безопасно управляет пользовательскими сеансами R и возвращает результаты клиенту.

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [Hello World в R и SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

<a name="bkmk_SSMSBasics"></a>

## <a name="create-some-simple-test-data"></a>Создание простых тестовых данных

Создайте небольшую таблицу тестовых данных, выполнив следующую инструкцию T-SQL:

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

После создания таблицы используйте следующую инструкцию, чтобы выполнить запрос к ней:
  
```sql
SELECT * FROM RTestData
```

**Результаты**

![Содержимое таблицы RTestData](media/quickstart-r-working-input-outputs-results-1.png)


## <a name="get-the-same-data-using-r-script"></a>Получение тех же данных с помощью скрипта R

После создания таблицы выполните следующую инструкцию:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

Он получает данные из таблицы, циклическом прохождении через среду выполнения R и возвращает значения с именем столбца, *NewColName*.

**Результаты**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**Комментарии**

+ Параметр *@language* определяет вызываемое расширение языка (в данном случае R).
+ В параметре *@script* определяются команды, передаваемые в среду выполнения R. Весь скрипт R должен быть заключен в этом аргументе в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее.
+ Данные, возвращаемые запросом, передаются в среду выполнения R, которая возвращает данные в SQL Server в качестве кадра данных.
+ Предложение WITH RESULT SETS определяет схему таблицы возвращаемых данных для SQL Server.

## <a name="change-input-or-output-variables"></a>Изменение входных или выходных переменных

В предыдущем примере использовались имена входных и выходных переменных по умолчанию — _InputDataSet_ и _OutputDataSet_. Чтобы определить входные данные, связанные с _InputDatSet_, следует использовать переменную *@input_data_1*.

В этом примере имена входных и выходных переменных для хранимой процедуры были изменены на *SQLOut* и *SQLIn*:

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```

Вы получили ошибку «объект SQL\_в не найден»? Это связано с тем, что R учитывает регистр. В данном примере скрипт R использует переменные *SQL_in* и *SQL_out*, однако параметры хранимой процедуры используют переменные *SQL_In* и *SQL_Out*.

Попытайтесь исправить **только** *SQL_In* переменной *@script* и повторно запустите хранимую процедуру.

Теперь вы получаете **различных** ошибка:

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

Отображается эта ошибка, так как вы сможете увидеть, как это часто при тестировании нового кода R. Это означает, что скрипт R выполнен успешно, но SQL Server получено нет данных, или получил неправильные или непредвиденные данные.

В этом случае схема вывода (строка, начинающаяся с **WITH**) указывает, что должен быть возвращен один столбец целочисленных данных, но так как R поместил данные в другую переменную, SQL Server не получил никаких данных и возникла ошибка. Чтобы устранить эту ошибку, исправьте имя второй переменной.

**Помните, эти требования!**

- Имена переменных должны соответствовать правилам для допустимых идентификаторов SQL.
- Важно учитывать порядок параметров. Чтобы использовать необязательные параметры *@input_data_1_name* и *@output_data_1_name*, сначала необходимо указать обязательные параметры *@input_data_1* и *@output_data_1*.
- В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а в дополнение к набору данных могут возвращаться выходные данные других типов. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. Далее в этом руководстве приведен простой пример, как это сделать.
- Инструкция `WITH RESULT SETS` определяет схему данных, возвращаемых SQL Server. Необходимо задать совместимые типы данных SQL для каждого столбца, возвращаемого из R. Также можно использовать определение схемы, чтобы задать имена для новых столбцов (не нужно использовать имена столбцов из кадра данных R). В некоторых случаях это предложение является необязательным; Попробуйте опустить его и посмотрим, что произойдет.

## <a name="generate-results-using-r"></a>Формирование результатов с помощью R

Можно также создать значения с помощью скрипта R и оставить пустой строку ввода запроса в _@input_data_1_ или использовать допустимую инструкцию SQL SELECT в качестве заполнителя и не использовать результаты SQL в скрипте R.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**Результаты**

![Результаты запроса с помощью @script как входные данные](media/quickstart-r-working-input-outputs-results-3.png)

## <a name="next-steps"></a>Следующие шаги

Изучите некоторые проблемы, которые могут возникнуть при передаче данных между R и SQL Server, таких как неявные преобразования и различия в табличных данных R и SQL.

> [!div class="nextstepaction"]
> [Краткое руководство: Обработка типов данных и объектов](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)