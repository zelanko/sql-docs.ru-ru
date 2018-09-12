---
title: Введение в пакет revoscalepy Python в службе машинного обучения SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f1d4d8bbb47c34fce61bdb95a3184a1d2b10f4d1
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889480"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>Знакомство с revoscalepy в машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** — новая библиотека Python, предоставляемых корпорацией Майкрософт для поддержки распределенных вычислений удаленных вычислений контексты и высокопроизводительных алгоритмов для разработчиков Python.

Он основан на **RevoScaleR** пакета для R, который был предоставлен в Microsoft R Server и служб R SQL Server и призван предоставить те же функциональные возможности:

+ Поддерживает несколько контекстов вычислений, удаленных и локальных
+ Предоставляет функции, эквивалентные функциям в RevoScaleR для преобразования данных и визуализации
+ Предоставляет версии Python алгоритмы машинного обучения RevoScaleR для распределенных или параллельной обработкой
+ Повышения производительности, включая использование библиотеки Intel math

MicrosoftML пакеты также предоставляются для R и Python. Дополнительные сведения см. в разделе [с помощью MicrosoftML в SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Версии и поддерживаемые платформы

**Revoscalepy** модуль доступен только при установке одного из следующих продуктов:

+ Службы машинного обучения, в SQL Server 2017
+ Microsoft Machine Learning Server 9.2.0 или более поздней версии

Чтобы получить последнюю версию revoscalepy, установите накопительный пакет обновления 1 для SQL Server 2017. Он включает множество улучшений в Python, включая:

+ Новая функция Python, `rx_create_col_info`, который получает сведения о схеме из источника данных SQL Server, таких как [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) для 
+ Усовершенствования [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) для поддержки параллельных сценарии с использованием `RxLocalParallel` контекста вычислений. 

## <a name="supported-functions-and-data-types"></a>Поддерживаемые функции и типы данных

В этом разделе представлен обзор типов данных Python и новые функции Python, поддерживаемые **revoscalepy** модуля, начиная с выпуска SQL Server 2017 CTP 2.0. 

Текущий список функций в библиотеках Python, выпущенных до настоящего времени см. следующие ссылки:

+ [revoscalepy для Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [microsoftml для Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Типы данных, источники данных и контекстов вычислений

SQL Server и Python используют разные типы данных в некоторых случаях. Список сопоставлений типов данных SQL и Python, см. в разделе [расширение Python](../concepts/extension-python.md).

Поддерживаемые источники данных для машинного обучения с Python в SQL Server включает в себя источники данных ODBC, базы данных SQL Server и локальные файлы, включая файлы XDF.

Создайте объект источника данных с помощью функций, перечисленных в следующей таблице. После определения источника данных, загрузки или преобразования данных с помощью соответствующей [ETL функция](#bkmk_etl).

> [!IMPORTANT]
> Многие имена функций были изменены с момента первоначального выпуска Python в CTP 2.0.

**Данные SQL Server**

+ Используйте [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) для определения источника данных из запроса или таблицы
+ Используйте [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) для создания контекста вычислений SQL Server
+ Используйте [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) для создания источника данных с помощью подключения ODBC

**revoscalepy** также поддерживает [источника данных XDF](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), которое используется для перемещения данных между памятью и другие источники данных.

> [!TIP]
> Если вы не знакомы с идея источников данных или контекстов вычислений, мы рекомендуем начать с изучения распределенных вычислений works для машинного обучения в [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Машинное обучение и статистические функции

В SQL Server 2017, начиная с CTP 2.0 включены следующие алгоритмы машинного обучения и Сводка функций RevoScaleR.

| Компонент| Описание|Примечания|
| ------ | ------ |------ |
|`rx_btrees` | Вписать стохастического градиента повышенных деревьев принятия решений|`rx_btrees_ex` в CTP 2.0|
|`rx_dforest` | Вписать классификации и регрессии леса принятия решений|`rx_dforest_ex` в CTP 2.0|
|`rx_dtree` | Вписать деревьев классификации и регрессии |`rx_dtree_ex` в CTP 2.0|
|`rx_lin_mod` | Создание линейной модели|`rx_lin_mod_ex` в CTP 2.0|
|`rx_logit` | создание модели логистической регрессии;|`rx_logit_ex` в CTP 2.0|
|`rx_predict` | Создание прогнозов из обученной модели|`rx_predict_ex` в CTP 2.0|
|`rx_summary` | Сформировать сводку по модели||

Новые алгоритмы машинного обучения также предоставляются в версии Python [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Компонент| Описание|
| ------ | ------ |
|`rx_fast_forest` |Создание модели леса принятия решений|
|`rx_fast_linear` | Линейная регрессия с стохастического парного координатного подъема|
|`rx_fast_trees` | Создать модель увеличивающегося дерева |
|`rx_logistic_regression` | создание модели логистической регрессии;|
|`rx_neural_network` | Создание настраиваемой нейронной сети |
|`rx_oneclass_svm` | Создает модель SVM в несбалансированных наборов данных, для использования при обнаружении аномалий|

> [!TIP]
> Многие из этих алгоритмов уже предоставляются как модули в машинном обучении Azure.

MicrosoftML для Python также включает множество преобразований и вспомогательные функции, такие как:

+ `rx_predict` Создает прогнозы на основе обученной модели и может использоваться для оценки в реальном времени
+ Добавление признаков функции образа
+ функции для обработки и тональности извлечение текста

Дополнительные сведения см. в разделе [введение в MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Сообществом Python использует соглашения о написании кода, которые могут отличаться от что вы привыкли, включая все строчные буквы и символы подчеркивания, а не смешанный регистр знаков для имен параметров. Кроме того, возможно вы определили, что **revoscalepy** библиотеки всегда производится в нижнем регистре. Правильно! Другой способ Python.
> 
> Ознакомьтесь с советами на Python справочная документация по Microsoft R: [Справка по функции Python][функциям Python](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Примеры

Вы можете выполнить код, который включает в себя **revoscalepy** функции локально или в удаленном контексте вычислений. Можно также запустить Python в SQL Server путем внедрения кода Python в хранимой процедуре.

При локальном запуске вы обычно выполнение скрипта Python из командной строки или из среды разработки Python и укажите контекст вычислений SQL Server с помощью одного из **revoscalepy** функции. Контекст удаленных вычислений можно использовать для весь код, или для отдельных функций. Например можно разгрузить Обучение модели на сервер, чтобы использовать последние данные и избежать перемещения данных.

Если вы хотите поместить полный сценарий Python в хранимой процедуре, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код как одну функцию, которая четко определенные входные и выходные данные. Входные и выходные данные должны быть **pandas** кадров данных. Если это сделано, можно вызвать хранимую процедуру из любого клиента, поддерживающего T-SQL, легко передать SQL-запросов в качестве входных данных и сохранить результаты в таблицы SQL. Например, см. в разделе [Analytics Python в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>С помощью удаленных контекстов вычислений

+ [Создание модели с помощью revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  В этом примере показано, как для запуска Python с использованием экземпляра SQL Server в качестве контекста вычисления.

### <a name="using-a-stored-procedure"></a>Использование хранимых процедур

+ [Запуск Python с помощью T-SQL](../tutorials/run-python-using-t-sql.md)

  Этот пример демонстрирует базовый механизм вызова скрипта Python, которое внедрено в хранимой процедуре.

### <a name="using-revoscalepy-with-microsoftml"></a>С помощью revoscalepy с MicrosoftML

Функции Python для MicrosoftML интегрированы с контексты вычисления и источников данных, которые предоставляются в revoscalepy. Таким образом можно использовать алгоритм MicrosoftML для определения и обучения модели на языке Python и использовать функции revoscalepy для выполнения кода Python, локально или в контексте вычислений SQl Server.

Импортировать модули в коде Python и затем ссылаться на отдельные функции, которые вам нужны.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Требования

Для выполнения кода Python в SQL Server, необходимо установить SQL Server 2017 вместе с функцию **служб машинного обучения**и поддержкой языка Python. Интеграция Python поддерживают не более ранних версиях SQL Server.

> [!NOTE]
> Дистрибутивы с открытым исходным кодом Python, не поддерживают контекстов вычислений SQL Server. Тем не менее если требуется для публикации и использования приложения Python из Windows, можно установить сервер машинного обучения Майкрософт без установки SQL Server. Дополнительные сведения см. в разделе [установить SQL Server 2017 сервера машинного обучения (изолированного)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Получить дополнительную справку

Полную документацию по этим интерфейсам API, будут доступны после выпуска продукта. В то же время мы рекомендуем установить ссылку на соответствующую функцию в библиотеки RevoScaleR или MicrosoftML.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

Можно получить справку о любой функции Python путем импорта модуля и последующего вызова `help()`. Например, на котором работают `help(revoscalepy)` из интерфейса IDE Python возвращает список всех функций в модуле revoscalepy с их сигнатурами.

При использовании инструментов Python для Visual Studio, можно использовать IntelliSense для получения справки синтаксиса и аргументов. Дополнительные сведения см. в разделе [поддержка Python в Visual Studio](http://docs.microsoft.com/visualstudio/python/installation)и скачать модуль, который соответствует вашей версии Visual Studio. Можно использовать Python с помощью Visual Studio 2015 и 2017 или более ранних версий.

## <a name="see-also"></a>См. также

[Учебники по Python](../tutorials/sql-server-python-tutorials.md)
