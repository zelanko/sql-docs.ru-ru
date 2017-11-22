---
title: "Работа с входными и выходными данными (R в быстрый запуск SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
- SQL
ms.assetid: 75480e5c-f37f-45b9-a176-67e08e9a9daf
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cb651d6541bbba7be03b74265ffae5dccdbdf9c9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="working-with-inputs-and-outputs-r-in-sql-quickstart"></a>Работа с входными и выходными данными (R в быстрый запуск SQL Server)

При необходимости выполнять код R в SQL Server требуется включить в системной хранимой процедуры, R-скрипта [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Эта хранимая процедура используется для запуска среды выполнения R в контексте SQL Server, который передает данные в R, безопасно управляет пользовательскими сеансами R и возвращает результаты клиенту.

## <a name="bkmk_SSMSBasics"></a>Создание простых тестовых данных

Создайте маленькую таблицу проверочных данных, выполнив следующую инструкцию T-SQL:

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

|col1|
|------|
|*1*|
|*10*|
|*100*|

## <a name="get-the-same-data-using-r-script"></a>Получение тех же данных с помощью скрипта R

После создания таблицы выполните следующую инструкцию:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

Получает данные из таблицы, выполняет круговой путь через среду выполнения R и возвращает значения с именем столбца, *NewColName*.

**Результаты**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**Комментарии**

+ В среде Management Studio табличные результаты возвращаются в области **Значения**. Сообщения, возвращаемые средой выполнения R, приводятся в области **Сообщения**.
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

Было появляется ошибка, «объекта SQL\_в не найден»? Это связано с тем, что R учитывает регистр. В данном примере скрипт R использует переменные *SQL_in* и *SQL_out*, однако параметры хранимой процедуры используют переменные *SQL_In* и *SQL_Out*.

Это происходит потому R с учетом регистра. В данном примере скрипт R использует переменные *SQL_in* и *SQL_out*, однако параметры хранимой процедуры используют переменные *SQL_In* и *SQL_Out*.
Попробуйте исправить **только** *SQL_In* переменной и повторно запустите хранимую процедуру.

Теперь вы получаете **другой** ошибка:

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

Мы отображается эта ошибка, так как вы сможете видеть его часто при тестировании нового кода R. Это означает, что скрипт R выполнено успешно, но SQL Server получил данные не или получении неправильного или непредвиденного данных.

В этом случае схема вывода (строка, начинающаяся с **WITH**) указывает, что должен быть возвращен один столбец целочисленных данных, но так как R поместил данные в другую переменную, SQL Server не получил никаких данных и возникла ошибка. Чтобы исправить ошибку, исправьте имя второй переменной.

**Помните, эти требования!**

- Имена переменных должны соответствовать правилам для допустимых идентификаторов SQL.
- Важно учитывать порядок параметров. Чтобы использовать необязательные параметры *@input_data_1_name* и *@output_data_1_name*, сначала необходимо указать обязательные параметры *@input_data_1* и *@output_data_1*.
- В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а в дополнение к набору данных могут возвращаться выходные данные других типов. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. Далее в этом руководстве приведен простой пример, как это сделать.
- Инструкция `WITH RESULT SETS` определяет схему данных, возвращаемых SQL Server. Необходимо задать совместимые типы данных SQL для каждого столбца, возвращаемого из R. Также можно использовать определение схемы, чтобы задать имена для новых столбцов (не нужно использовать имена столбцов из кадра данных R). В некоторых случаях это предложение является необязательным. Попробуйте, пропустив его и посмотрите, что произойдет.

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

*Col1*
*hello*
<code>   </code>
*world*

## <a name="next-lesson"></a>Следующее занятие

Изучите некоторые из проблем, которые могут возникнуть при передаче данных между R и SQL Server, например неявные преобразования и различия в табличных данных R и SQL.

[Типы и объекты данных R и SQL](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
