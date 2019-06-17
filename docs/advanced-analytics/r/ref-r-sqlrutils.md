---
title: вспомогательные функции для работы с sqlrutils - службы машинного обучения SQL Server
description: Используйте библиотеку sqlrutils функция в SQL Server 2016 R Services и службы машинного обучения SQL Server 2017 с R для создания хранимых процедур, содержащих R-скрипт.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7ccc3ad494658fc7a8f9c67472aecb1c4cddb7da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641753"
---
# <a name="sqlrutils-r-library-in-sql-server"></a>sqlrutils (библиотека R в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Пакет **sqlrutils** предоставляет пользователям R механизм для помещения скриптов R в хранимую процедуру T-SQL, регистрации этой хранимой процедуры с базой данных и ее запуска из среды разработки R. 

Преобразование кода R для выполнения в рамках одной хранимой процедуры позволяет более эффективно использовать службы SQL Server R Services, которые требуют внедрить скрипт R в качестве параметра в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Пакет **sqlrutils** помогает создать такой внедренный скрипт R и правильно настроить соответствующие параметры.

Пакет **sqlrutils** выполняет следующие задачи.

- Сохраняет созданный скрипт T-SQL в виде строки внутри структуры данных R.
- При необходимости создает SQL-файл для скрипта T-SQL, который можно изменить или выполнить, чтобы создать хранимую процедуру.
- Регистрирует созданную хранимую процедуру в экземпляре SQL Server из среды разработки R.

Вы также можете выполнить хранимую процедуру из среды R, передав параметры с правильным форматом и обработав результаты. Или вы можете использовать хранимую процедуру из SQL Server для поддержки стандартных сценариев интеграции базы данных, таких как извлечение, преобразование и загрузка, обучение модели и оценка большого объема.

  > [!NOTE]
  > Если планируется выполнить хранимую процедуру из среды R путем вызова функции *executeStoredProcedure* , следует использовать поставщик ODBC 3.8, например драйвер ODBC 13 для SQL Server.  
  
## <a name="full-reference-documentation"></a>Полная справочная документация

**Sqlrutils** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных sqlrutils функций](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) публикуется только в одном месте в разделе [ссылку R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="functions-list"></a>Список функций

В следующем разделе приведены общие сведения о функции, которые можно вызывать из **sqlrutils** пакета для разработки хранимой процедуре, содержащей внедренный код R. Сведения о параметрах для каждого метода или функции см. в справке R для пакета: `help(package="sqlrutils")`

|Компонент | Описание |
|------|-------------|
|[executeStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/executestoredprocedure)| Выполнение хранимой процедуры SQL.|
|[getInputParameters](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/getinputparameters)| Получите список входных параметров для хранимой процедуры.| 
|[InputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputdata)| Определяет источник данных в SQL Server, который будет использоваться в кадре данных R. Укажите имя data.frame для хранения входных данных и запрос для получения данных или значение по умолчанию. Поддерживаются только простые запросы SELECT. | 
|[InputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputparameter)| Определяет отдельный входной параметр, который будет внедрен в скрипт T-SQL. Необходимо указать имя параметра и его тип данных R.| 
|[OutputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputdata)| Cоздает объект промежуточных данных, который требуется, когда функция R возвращает список, содержащий data.frame. Объект *OutputData* используется для хранения имени отдельного data.frame, полученного из списка.| 
|[OutputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputparameter) | Cоздает объект промежуточных данных, который требуется, когда функция R возвращает список. Объект *OutputParameter* хранит имя и тип данных для одного элемента списка при условии, что он **не** является кадром данных. |
|[registerStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/registerstoredprocedure) | Зарегистрируйте хранимую процедуру с базой данных.|
|[setInputDataQuery](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputdataquery)| Назначьте запрос к параметру входных данных хранимой процедуры.| 
|[setInputParameterValue](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputparametervalue)| Присвоить значение входного параметра хранимой процедуры.| 
|[Хранимая процедура](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/storedprocedure)| Объект хранимой процедуры.|


## <a name="how-to-use-sqlrutils"></a>Как использовать sqlrutils

**Sqlrutils** функции библиотеки необходимо запустить на компьютере с SQL Server машинного обучения с использованием R. При работе на клиентской рабочей станции, задайте контекст удаленных вычислений для выполнения shift для SQL Server. Рабочий процесс использования этот пакет включает следующие шаги:

+ Задать параметры процедуры (входные данные, выходные данные или оба) 
+ Создать и зарегистрировать хранимую процедуру    
+ Выполнение хранимой процедуры  

В сеансе R, загрузить **sqlrutils** из командной строки, введя `library(sqlrutils)`.

> [!Note]
> Вы можете загрузить эту библиотеку на компьютере, который не установлен SQL Server (например, на экземпляре R Client), если изменить контекст вычислений на SQL Server и выполните код в этом контексте вычислений.


### <a name="define-stored-procedure-parameters-and-inputs"></a>Определение параметров хранимых процедур и входных данных

`StoredProcedure` является основным конструктором, используемым для создания хранимой процедуры. Этот конструктор создает объект *хранимой процедуры SQL Server* и при необходимости создает текстовый файл, содержащий запрос, который можно использовать для создания хранимой процедуры с помощью команды T-SQL. 

При необходимости функция *StoredProcedure* может зарегистрировать хранимую процедуру с помощью указанного экземпляра и базы данных.

+ Используйте аргумент `func` для указания допустимой функции R. Все переменные, которые использует функция, должны быть определены внутри функции либо представления в виде входных параметров. Эти параметры могут включать не более одного кадра данных.

+ Функция R должна возвращать кадр данных, именованный список или значение NULL. Если функция возвращает список, он может содержать не более одного data.frame.

+ Используйте аргумент `spName` для указания имени создаваемой хранимой процедуры.

+ Можно передать необязательные входные и выходные параметры с помощью объектов, созданных следующими вспомогательными функциями: `setInputData`, `setInputParameter`и `setOutputParameter`.

+  При необходимости используйте `filePath` для указания пути и имени создаваемого SQL-файла. Этот файл можно запустить на экземпляре SQL Server для создания хранимой процедуры с помощью T-SQL.

+ Для определения сервера и базы данных, где будет сохранена хранимая процедура, используйте аргументы `dbName` и  `connectionString`.

+ Чтобы получить список объектов *InputData* и *InputParameter* , которые использовались для создания определенного объекта *StoredProcedure* , вызовите `getInputParameters`. 

+ Чтобы зарегистрировать хранимую процедуру в указанной базе данных, используйте `registerStoredProcedure`.

Объект хранимой процедуры обычно не имеет связанных с ним данных или значений, если только не указано значение по умолчанию. Данные не извлекаются до выполнения хранимой процедуры. 

### <a name="specify-inputs-and-execute"></a>Укажите входные данные и выполнение

+ Используйте `setInputDataQuery` для назначения запроса объекту *InputParameter* . Например, если вы создали объект хранимой процедуры в R, можно использовать `setInputDataQuery` для передачи аргументов в *StoredProcedure* для выполнения хранимой процедуры с нужными входными данными.

+ Используйте `setInputValue` для назначения конкретного значения параметру, сохраненному в виде объекта *InputParameter* . Затем передайте объект параметра и его назначение значения в *StoredProcedure* , чтобы выполнить хранимую процедуру с заданными значениями.

+ Используйте `executeStoredProcedure` для выполнения хранимой процедуры, определенной в виде объекта *StoredProcedure* . Вызывайте эту функцию только при выполнении хранимой процедуры из кода R. Не используйте ее при запуске хранимой процедуры из SQL Server с помощью T-SQL.

> [!NOTE]
> Функции *executeStoredProcedure* требуется поставщик ODBC 3.8, например драйвер ODBC 13 для SQL Server.  

## <a name="see-also"></a>См. также

[Создание хранимой процедуры с помощью sqlrutils](how-to-create-a-stored-procedure-using-sqlrutils.md)

