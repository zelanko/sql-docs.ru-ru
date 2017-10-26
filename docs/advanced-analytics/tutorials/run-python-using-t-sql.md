---
title: "Запустите Python с помощью T-SQL | Документы Microsoft"
ms.custom: 
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- Python
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: f2eba50d5c5e57025462c46b38fc0ddbfc947ea0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="run-python-using-t-sql"></a>Выполнения Python, с помощью T-SQL

В этом примере показано, как выполнить простой сценарий Python в SQL Server с помощью хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

## <a name="step-1-create-the-test-data-table"></a>Шаг 1. Создание таблицы данных теста

Во-первых вы создадите некоторые дополнительные данные для использования при сопоставлении названия дней недели с источником данных. Выполните следующую инструкцию T-SQL для создания таблицы.

```SQL
CREATE TABLE PythonTest (
    [DayOfWeek] varchar(10) NOT NULL,
    [Amount] float NOT NULL
    )
GO

INSERT INTO PythonTest VALUES
('Sunday', 10.0),
('Monday', 11.1),
('Tuesday', 12.2),
('Wednesday', 13.3),
('Thursday', 14.4),
('Friday', 15.5),
('Saturday', 16.6),
('Friday', 17.7),
('Monday', 18.8),
('Sunday', 19.9)
GO
```

## <a name="step-2-run-the-hello-world-script"></a>Шаг 2. Запустите скрипт «Hello World»

Следующий код загружает исполняемый файл Python, передает входных данных и обновляет название дня недели в таблице число, представляющее индекс день недели для каждой строки входных данных.

Запишите параметр  *@RowsPerRead* . Этот параметр задает число строк, которые передаются среды выполнения Python из SQL Server.

Python библиотеки анализа данных, известных как **pandas**, необходим для передачи данных в SQL Server и включается по умолчанию с компьютера службы обучения.

```sql
DECLARE @ParamINT INT = 1234567
DECLARE @ParamCharN VARCHAR(6) = 'INPUT '

print '------------------------------------------------------------------------'
print 'Output parameters (before):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)

print 'Dataset (before):'
SELECT * FROM PythonTest

print '------------------------------------------------------------------------'
print 'Dataset (after):'
DECLARE @RowsPerRead INT = 5

execute sp_execute_external_script 
@language = N'Python',
@script = N'
import sys
import os
print("*******************************")
print(sys.version)
print("Hello World")
print(os.getcwd())
print("*******************************")
if ParamINT == 1234567:
       ParamINT = 1
else:
       ParamINT += 1

ParamCharN="OUTPUT"
OutputDataSet = InputDataSet

global daysMap

daysMap = {
       "Monday" : 1,
       "Tuesday" : 2,
       "Wednesday" : 3,
       "Thursday" : 4,
       "Friday" : 5,
       "Saturday" : 6,
       "Sunday" : 7
       }

OutputDataSet["DayOfWeek"] = pandas.Series([daysMap[i] for i in OutputDataSet["DayOfWeek"]], index = OutputDataSet.index, dtype = "int32")
', 
@input_data_1 = N'SELECT * FROM PythonTest', 
@params = N'@r_rowsPerRead INT, @ParamINT INT OUTPUT, @ParamCharN CHAR(6) OUTPUT',
@r_rowsPerRead = @RowsPerRead,
@paramINT = @ParamINT OUTPUT,
@paramCharN = @ParamCharN OUTPUT
with result sets (("DayOfWeek" int null, "Amount" float null))

print 'Output parameters (after):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)
GO
```

> [!TIP]
> Параметры для этой хранимой процедуры описаны более подробно в этом кратком руководстве: [R с помощью кода в T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md).

## <a name="step-3-view-the-results"></a>Шаг 3. Просмотр результатов

Хранимая процедура получает исходные данные, применяется сценарий Python и затем возвращает измененные данные в **результатов** области среды Management Studio или другого средства запросов SQL.


|DayOfWeek (раньше)| Сумма|DayOfWeek (теперь) |
|-----|-----|-----|
|Воскресенье|10|7|
|Понедельник|11.1|1|
|Вторник|12.2|2|
|Среда|13.3|3|
|Четверг|14.4|4|
|Пятница|15.5|5|
|Суббота|16.6|6|
|Пятница|17.7|5|
|Понедельник|18.8|1|
|Воскресенье|19.9|7|

Сообщения о состоянии или ошибок, возвращаемых в консоль Python, возвращаются в виде сообщения в **запроса** окна. Ниже приведен фрагмент выходных данных, которые можно увидеть.

*Образец результатов*

```
Output parameters (before):
ParamINT=1234567
ParamCharN=INPUT 
Dataset (before):

(10 rows affected)

Dataset (after):
STDOUT message(s) from external script: 
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

(10 rows affected)
Output parameters (after):
ParamINT=2
ParamCharN=OUTPUT
```

+ **Сообщение** выходные данные содержат рабочего каталога, используемого для выполнения скриптов. В этом примере MSSQLSERVER01 ссылается на учетную запись работника, выделенной с помощью SQL Server для управления заданием. 

    Идентификатор GUID — это имя временной папки, созданный во время выполнения скрипта для хранения данных и скрипт артефактов. Эти временные папки защищены с помощью SQL Server и очищаются, объект задания Windows после завершения скрипта.

+ Раздел, содержащий сообщение «Hello World» выводит два раза. Это происходит потому, что значение  *@RowsPerRead*  было присвоено значение 5 и 10 строк в таблице; таким образом, два вызова Python необходимы для обработки всех строк в таблице.

    В вашей рабочей среде выполняется рекомендуется поэкспериментировать с различными значениями, чтобы определить максимальное число строк, которые должны быть переданы в каждом пакете. Оптимальное количество строк зависит от данных и влияет количество столбцов в наборе данных и тип данных, которые вы передаете.

## <a name="resources"></a>Ресурсы

См. Эти дополнительные Python образцы и учебники по Дополнительные советы и демонстрации начала до конца.

+ [Использовать Python revoscalepy для создания модели](use-python-revoscalepy-to-create-model.md)
+ [Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

## <a name="troubleshooting"></a>Устранение неполадок

Если не удается найти хранимую процедуру `sp_execute_external_script`, это означает, что вы, возможно, не была завершена настройка экземпляра для поддержки выполнения внешнего сценария. После запуска программы установки SQL Server 2017 г. и выбора Python как машинного обучения язык, необходимо явным образом включить функции с помощью `sp_configure`, а затем перезапустите экземпляр. Дополнительные сведения см. в разделе [установки службы обучения машины с Python](../python/setup-python-machine-learning-services.md).
