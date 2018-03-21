---
title: "Знакомство с revoscalepy | Документы Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 2649596abecfd92d40a860e743c867e0ff80ed26
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="introducing-revoscalepy"></a>Знакомство с приложением revoscalepy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** представляет собой новую библиотеку, предоставляемых корпорацией Майкрософт для поддержки распределенных вычислений удаленных вычислений контексты и высокопроизводительных алгоритмов для Python.

Он основан на **RevoScaleR** пакет R, который был предоставлен в Microsoft R Server и SQL Server R Services и предполагается предоставляют те же функциональные возможности:

+ Поддерживает несколько контекстов вычислений, удаленные и локальные
+ Предоставляет функции, эквивалентные функциям в RevoScaleR для преобразования данных и визуализации
+ Предоставляет версии Python RevoScaleR алгоритмов машинного обучения для распределенных или параллельной обработкой
+ Повышения производительности, включая использование библиотеки Intel math

Пакеты MicrosoftML также предоставляются R и Python. Дополнительные сведения см. в разделе [с помощью MicrosoftML в SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Версии и поддерживаемые платформы

**Revoscalepy** модуля доступен только при установке одного из следующих продуктов:

+ Машинное обучение Services в SQL Server 2017 г.
+ Microsoft Server обучения машины 9.2.0 или более поздней версии

Чтобы получить последнюю версию revoscalepy, установите накопительный пакет обновления 1 для 2017 г. SQL Server. Он включает множество улучшений в Python, включая:

+ Новая функция Python, `rx_create_col_info`, который получает сведения о схеме из источника данных SQL Server как [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) для 
+ Усовершенствования [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) для поддержки параллельных сценариях с использованием `RxLocalParallel` контекста вычислений. 

## <a name="supported-functions-and-data-types"></a>Поддерживаемые функции и типы данных

В этом разделе содержится обзор типов данных Python и новые функции Python, поддерживаемые **revoscalepy** модуля, начиная с выпуска SQL Server 2017 г CTP 2.0. 

Новейший список функций в библиотеках Python, выпущенных до настоящего времени найти по следующим ссылкам:

+ [revoscalepy для Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [microsoftml для Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Типы данных, источники данных и контекстов вычислений

SQL Server и Python используют разные типы данных в некоторых случаях. Список сопоставлений типов данных SQL и Python см. в разделе [Python библиотек и типы данных](python-libraries-and-data-types.md).

Источники данных, поддерживаемые для машинного обучения с Python в SQL Server содержит источники данных ODBC, базы данных SQL Server и локальных файлов, включая файлы XDF.

Создайте объект источника данных с помощью функций, перечисленных в следующей таблице. После определения источника данных, загрузить или преобразования данных с помощью соответствующей [ETL функция](#bkmk_etl).

> [!IMPORTANT]
> Многие функции имена были изменены с момента первоначального выпуска Python в CTP-версии 2.0.

**Данные SQL Server**

+ Используйте [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) для определения источника данных из запроса или таблицы
+ Используйте [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) для создания контекста вычислений SQL Server
+ Используйте [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) для создания источника данных из соединения ODBC

**revoscalepy** также поддерживает [источника данных XDF](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), используемые для перемещения данных между памяти и других источников данных.

> [!TIP]
> Если вы не знакомы с представление источников данных или контекстов вычислений, мы рекомендуем начать с чтения о распределенной вычислительной работы для машинного обучения в [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Машинное обучение и статистические функции

Следующие алгоритмы машинного обучения и Сводка функций из RevoScaleR, включаются в SQL Server 2017 г., начиная с CTP-версии 2.0.

| Функция| Описание|Примечания|
| ------ | ------ |------ |
|`rx_btrees` | Вписать вероятностного градиентного повышенные деревья принятия решений|`rx_btrees_ex` в CTP 2.0.|
|`rx_dforest` | Вписать классификации и регрессии леса принятия решений|`rx_dforest_ex` в CTP 2.0.|
|`rx_dtree` | Соответствия деревьев классификации и регрессии |`rx_dtree_ex` в CTP 2.0.|
|`rx_lin_mod` | Создать модель линейный|`rx_lin_mod_ex` в CTP 2.0.|
|`rx_logit` | создание модели логистической регрессии;|`rx_logit_ex` в CTP 2.0.|
|`rx_predict` | Создание прогнозов из обученной модели|`rx_predict_ex` в CTP 2.0.|
|`rx_summary` | Сформировать сводку о модели||

Версия Python также предоставляются новые алгоритмы машинного обучения [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Функция| Описание|
| ------ | ------ |
|`rx_fast_forest` |Создание модели леса принятия решений|
|`rx_fast_linear` | Линейной регрессии с помощью вероятностного Восхождение двух координат|
|`rx_fast_trees` | Создать модель повышенного дерева принятия решений |
|`rx_logistic_regression` | создание модели логистической регрессии;|
|`rx_neural_network` | Создание настраиваемой нейронной сети |
|`rx_oneclass_svm` | Создает модель SVM несбалансированных набору данных, для использования при обнаружении аномалий|

> [!TIP]
> Многие из этих алгоритмов уже указано как модули в машинном обучении Azure.

MicrosoftML для Python также включает множество преобразований и вспомогательных функций, таких как:

+ `rx_predict` для создания прогнозов из обученной модели и может использоваться для оценки в реальном времени
+ функции featurization изображения
+ функции для обработки и мнений извлечение текста

Дополнительные сведения см. в разделе [введение в MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Сообщество Python использует соглашения о написании кода, которые может отличаться от том, что вы привыкли, включая все строчные буквы и знаки подчеркивания, а не верблюжий для имен параметров. Кроме того, возможно вы заметили, **revoscalepy** библиотеки всегда производится в нижнем регистре. Правильно! Другое соглашение о Python.
> 
> См. Советы по Python справочная документация по Microsoft R: [Справка функции Python][функциям Python](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Примеры

Можно запустить код, который содержит **revoscalepy** функции локально или в контексте удаленных вычислений. Можно также запустить Python в SQL Server путем внедрения кода Python в хранимой процедуре.

При выполнении локально, обычно сценарий Python из командной строки или из среды разработки Python и укажите контекста вычислений SQL Server с помощью одного из **revoscalepy** функции. Контекста удаленных вычислений можно использовать для всего кода или для отдельных функций. Например может потребоваться разгрузки Обучение модели на сервере для использования последних данных и избежать перемещения данных.

Если вы хотите поместить полный сценарий Python в хранимой процедуре [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код, в виде одной функции, четко определенное входов и выходов. Входные и выходные данные должны быть **pandas** кадров данных. После этого, можно вызвать хранимую процедуру из любого клиента, который поддерживает T-SQL, легко передавать запросы SQL в качестве входных данных и сохранить результаты в таблицы SQL. Пример см. в разделе [Analytics Python в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>С помощью контекстах удаленных вычислений

+ [Создать модель с помощью revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  В этом примере показано, как Python, используя экземпляр SQL Server в контексте выполнения.

### <a name="using-a-stored-procedure"></a>С помощью хранимой процедуры

+ [Выполнения Python, с помощью T-SQL](../tutorials/run-python-using-t-sql.md)

  Этот пример демонстрирует базовый механизм вызова сценарий Python, внедренного в хранимой процедуре.

### <a name="using-revoscalepy-with-microsoftml"></a>Использование revoscalepy с MicrosoftML

Функции Python для MicrosoftML интегрированы с контекстов вычислений и источники данных, которые содержатся в revoscalepy. Таким образом можно использовать алгоритм MicrosoftML для определения и обучения модели на Python и использовать функции revoscalepy для выполнения кода Python, локально или в контексте вычислений SQl Server.

Импортировать модули в коде Python и затем ссылаться на отдельные функции, что нужно.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Требования

Для выполнения кода Python в SQL Server, необходимо установить 2017 г. SQL Server вместе с функцию **службы обучения машины**и включен языка Python. SQL Server более ранних версий не поддерживают интеграции Python.

> [!NOTE]
> Контексты вычислений SQL Server не поддерживают дистрибутивов открытым исходным кодом Python. Тем не менее если требуется для публикации и использования приложений Python из Windows, можно установить Microsoft Server обучения машины без установки SQL Server. Дополнительные сведения см. в разделе [установки сервера SQL Server 2017 г машины обучения (автономный)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Дополнительная справка

Полную документацию по этим API будут доступны после выпуска продукта. В то же время рекомендуется ссылаться на соответствующей функции в библиотеках RevoScaleR или MicrosoftML.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

Можно получить справку по любой функции Python путем импорта модуля и вызова `help()`. Например, на котором работают `help(revoscalepy)` возвращает список всех функций в модуле revoscalepy с подписями из интерфейс IDE Python.

При использовании средства Python для Visual Studio, можно использовать IntelliSense для получения справки синтаксиса и аргументов. Дополнительные сведения см. в разделе [поддержка Python в Visual Studio](http://docs.microsoft.com/visualstudio/python/installation)и загрузить модуль, который соответствует вашей версии Visual Studio. Можно использовать Python с Visual Studio 2015 и 2017 г. или более ранних версий.

## <a name="see-also"></a>См. также

[Учебники по Python](../tutorials/sql-server-python-tutorials.md)
