---
title: "Обновить - Advanced Analytics для документации по SQL Server | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации, Advanced Analytics в Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fb6185aae04a1fb53a4db03cbab267e3f52dc779
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Новые и недавно обновленные: Advanced Analytics для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-07-18** &nbsp; - в - &nbsp; **2017 г-09-11**
- *Предметной области:* &nbsp; **Advanced Analytics для SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Следующие ссылки на новые статьи, которые недавно были добавлены.


1. [Как выполнять оценки в реальном времени или собственного оценки в SQL Server](r/how-to-do-realtime-scoring.md)
2. [Установить предварительно обученные машинного обучения моделей, основанных на SQL Server](r/install-pretrained-models-sql-server.md)
3. [Собственная оценка](sql-native-scoring.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

Compact представлены ссылки на обновленные статьи, которые перечислены в разделе отрывки.

1. [Настройка службы обучения машины Python (в базе данных)](#TitleNum_1)
2. [Знакомство с приложением revoscalepy](#TitleNum_2)
3. [Различия в машинном обучении между выпусками SQL Server](#TitleNum_3)
4. [Ввода в эксплуатацию кода R (обучения Machine Services)](#TitleNum_4)
5. [Производительность служб R: результаты и ресурсы](#TitleNum_5)
6. [Производительность служб R - оптимизация данных](#TitleNum_6)
7. [Управление пакетами R для SQL Server](#TitleNum_7)
8. [Настройка служб машинного обучения SQL Server (в базе данных)](#TitleNum_8)
9. [Конфигурация SQL Server для использования с помощью R](#TitleNum_9)
10. [Настройка производительности для R в SQL Server](#TitleNum_10)
11. [Сценарии и шаблоны решений для обработки и анализа данных](#TitleNum_11)
12. [Новые возможности службы обучения машины в SQL Server](#TitleNum_12)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-set-up-python-machine-learning-services-in-databasepythonsetup-python-machine-learning-servicesmd"></a>1. &nbsp;[Установка Python машины обучения служб (в базе данных)](python/setup-python-machine-learning-services.md)

*Обновлено: 2017 г-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 263.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 fbe2ef55a5caecd64bb21ce854617a10b2d65567 8cd65baf77f27db00a0a4f07f3129a4231edb48b  (PR=3084  ,  Filename=setup-python-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=05976158e43d7dfafaf02289462d1537f5beeb36) -->



     [Modify the user account pool for SQL Server R Services--../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Если вы используете SQL Server Standard Edition и могут не регулятора ресурсов, можно использовать динамические административные представления и расширенные события для управления ресурсами сервера. Можно также использовать отслеживание событий Windows для этой цели. Дополнительные сведения см. в разделе [мониторинг и управление R Services--... /r/Managing-and-Monitoring-r-Solutions.MD).

**Обновление машинного обучения компонентов**


При установке службы обучения машины с помощью 2017 г. SQL Server вы получаете версии компонентов во время выпуска была опубликована. Каждый раз, исправление или обновление экземпляра SQL Server, машины обучения обновление компонентов также.

Вы можете обновить машинного обучения компонентов по расписанию быстрее, чем поддерживается только в версиях SQL Server, установив сервер обучения Майкрософт машины. После этого, можно также получить любые новые функции поддерживаются в последнем выпуске машины обучения Server, такие как:

+ Обновления, пакеты Python для [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml для Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Обученная моделей](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) для классификации и текст анализ образов.

Сведения о том, как обновить экземпляр см. в разделе [R Обновление компонентов с помощью привязки--... \r\use-sqlbindr-exe-to-Upgrade-an-instance-of-SQL-Server.MD).

> [!NOTE]
>
> В текущей версии содержит последнюю версию всех компонентов машины обучения. Таким образом несмотря на то, что обновление через сервер обучения Майкрософт машины поддерживается для SQL Server 2017 г., обновления, к которым в настоящее время доступна применяется только к экземплярам SQL Server 2016.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>2. &nbsp;[Знакомство с revoscalepy](python/what-is-revoscalepy.md)

*Обновлено: 2017 г-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 79.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a d2eac3313a74bc5d5afd754fc357b3693e6801e1  (PR=2939  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



| (column_1) | (Столбец_2) | (column_3) |
| :-- | :-- | :-- |
|`rx_btrees` | Вписать вероятностного градиентного повышенные деревья принятия решений|`rx_btrees_ex`в CTP 2.0.|
|`rx_dforest` | Вписать классификации и регрессии леса принятия решений|`rx_dforest_ex`в CTP 2.0.|
|`rx_dtree` | Соответствия деревьев классификации и регрессии |`rx_dtree_ex`в CTP 2.0.|
|`rx_lin_mod` | Создать модель линейный|`rx_lin_mod_ex`в CTP 2.0.|
|`rx_logit` | создание модели логистической регрессии;|`rx_logit_ex`в CTP 2.0.|
|`rx_predict` | Создание прогнозов из обученной модели|`rx_predict_ex`в CTP 2.0.|
|`rx_summary` | Сформировать сводку о модели||

Версия Python также предоставляются новые алгоритмы машинного обучения [MicrosoftML](https://docs.microsoft.com/en-us/r-server/python-reference/microsoftml/microsoftml-package):

| Функция| Description|
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

+ `rx_predict`для создания прогнозов из обученной модели и может использоваться для оценки в реальном времени
+ функции featurization изображения
+ функции для обработки и мнений извлечение текста

Дополнительные сведения см. в разделе [введение в MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Сообщество Python использует соглашения о написании кода, которые может отличаться от том, что вы привыкли, включая все строчные буквы и знаки подчеркивания, а не верблюжий для имен параметров. Кроме того, возможно вы заметили, **revoscalepy** библиотеки всегда производится в нижнем регистре. Правильно! Другое соглашение о Python.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-differences-in-machine-learning-features-between-editions-of-sql-serverrdifferences-in-r-features-between-editions-of-sql-servermd"></a>3. &nbsp;[Различия в возможностях обучения машины между выпусками SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

*Обновлено: 2017 г-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 47.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5890e212063f3ef228e69afe54e226320d2467f 4e0357701d960c0b8dbda1ac8d56a82f3335c77f  (PR=2964  ,  Filename=differences-in-r-features-between-editions-of-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



     Only Express Edition with Advanced Services includes the machine learning features. The performance limitations are similar to Standard Edition. Web edition is not intended for tasks such as creating machine learning models; however, you can use the PREDICT function to perform scoring using models trained elsewhere.

-   **База данных SQL Azure**

     Функции обучения компьютера, например R и сценариев Python в настоящее время не поддерживается в базе данных SQL Azure.

     Дополнительные сведения и объявления о когда этот компонент будет доступен, см. в блоге SQL Server: [Python в 2017 г. SQL Server: усиленной в базе данных машинного обучения](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


**Языки, поддерживаемые в все выпуски**


На следующих языках обучения машины поддерживаются для всех выпусков:

+ SQL Server 2017 г.: R и Python
+ SQL Server 2016: Только для чтения

Microsoft R Open входит в состав всех выпусков.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-operationalize-r-code-machine-learning-servicesroperationalizing-your-r-codemd"></a>4. &nbsp;[R ввода в эксплуатацию кода (обучения Machine Services)](r/operationalizing-your-r-code.md)

*Обновлено: 2017 г-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e11d9a5db93932ec89ca96b5337aa4ea03c1d13 0779f06444b5b73ae2dff8bc190d0e388b4ae8e7  (PR=2660  ,  Filename=operationalizing-your-r-code.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



+ [В реальном времени —... / scoring.md режиме реального времени) оценки, оптимизированный для небольших пакетов
+ Однострочный оценки для вызова из приложения
+ [Собственный оценки--... / sql native-scoring.md), для быстрого пакетный прогноз из SQL Server без вызова R

В этом пошаговом руководстве приведены примеры оценки с помощью хранимой процедуры в пакете и режимов одной строки.

+ [Сквозной Пошаговое руководство для обработки и анализа данных для R в SQL Server... / tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Видеть эти шаблоны решений примеры интеграции оценки в приложении:

+ [Прогнозирование розничных продаж](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Мошенничества](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [Кластеризация клиента](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

**Повышение производительности и масштабируемости**


Хотя язык R с открытым кодом имеет ограничения, пакет RevoScaleR API-интерфейсы могут работать с большими наборами данных и использовать преимущества многопоточных, многоядерных несколькими процессами вычислений в базе данных.

Если решение R использует сложные агрегаты или большие наборы данных, можно использовать высокоэффективные в памяти агрегаты и индексы columnstore SQL Server и программный код R обработку статистических вычислений и оценки.

Дополнительные сведения о способах повышения производительности в SQL Server машинного обучения см. в разделе:

+ [Настройка производительности для SQL Server R Services--... /.. / advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Советы по оптимизации производительности и рекомендации](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Адаптировать код R для других платформ или контекстов вычислений**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-performance-for-r-services-results-and-resourcesrperformance-case-study-r-servicesmd"></a>5. &nbsp;[Производительности для служб R: результаты и ресурсы](r/performance-case-study-r-services.md)

*Обновлено: 2017 г-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 282.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 40c8cd255ead88edc60531d45dd0377ecbaf7c9b eeca5eed96e2223508910b246dbff18173eecea3  (PR=2565  ,  Filename=performance-case-study-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



Пакеты MicrosoftML и RevoScaleR, использованных для обучения прогнозной модели в сложные решения R, с большими наборами данных. Запросы SQL и код R были идентичными. Все тесты проводились на одной виртуальной Машины Azure с установленным сервером SQL Server. Автор затем сравнивается оценки времени с и без этих оптимизаций, предоставляемым SQL Server:

- Таблицы в памяти
- Soft-NUMA
- Регулятор ресурсов

Чтобы оценить влияние на выполнение скрипта R программной архитектуры NUMA, команды обработки и анализа данных тестировать решение на виртуальной машине Azure с 20 физических ядер. На этих физических ядер на четыре программной архитектуры NUMA были созданы автоматически, таким образом, что каждый узел содержит пять ядер.

В случае соответствия resume для оценки влияния на заданий R была применена сопоставить ЦП. Четыре **пулы ресурсов SQL** и четыре **внешних пулов ресурсов** были созданы, чтобы убедиться, что в каждом узле, будет использоваться тот же набор процессоров указан процессоров.

Каждый из пулов ресурсов был назначен различные группы рабочей нагрузки, чтобы оптимизировать использование оборудования. Причина заключается в Soft-NUMA и сходство ЦП невозможно разделить физической памяти в физических узлов NUMA; Таким образом по определению все, основанных на одном физическом узле NUMA узлов NUMA мягкой необходимо использовать память в одном блоке памяти операционной системы. Другими словами является без сходства процессора и памяти.

Процесс был использован для создания такой конфигурации:

1. Сократите объем памяти по умолчанию для SQL Server.

2. Создайте четыре новые пулы для выполнения заданий R в параллельном режиме.

3. Таким образом, что каждая группа рабочей нагрузки связана с пулом ресурсов, создайте четыре группы рабочей нагрузки.

4. Перезапустите регулятора ресурсов с новой группы рабочей нагрузки и назначений.

5. Создайте функцию-классификатор, определяемые пользователем (UDF) для назначения различных задач на группы другой рабочей нагрузки.

6. Обновите конфигурацию регулятора ресурсов для использования функции для группы рабочей нагрузки.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-performance-for-r-services---data-optimizationrr-and-data-optimization-r-servicesmd"></a>6. &nbsp;[Производительности для служб R - оптимизация данных](r/r-and-data-optimization-r-services.md)

*Обновлено: 2017 г-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 107.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2ae2e54e8c5c8a3ec92fd2017088dd6ee879a9a1 9cb06bdce4ad6dfa2e9dc19da49103a6cd9817b3  (PR=2565  ,  Filename=r-and-data-optimization-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



> Если таблицы в источнике данных, а не запрос, R Services используется эвристическими для определения необходимых столбцов для выборки из таблицы; Однако такой подход вряд ли приведет параллельного выполнения.

Чтобы убедиться, что данные можно проанализировать в параллельном режиме, следует заключить запрос, используемый для извлечения данных таким образом, что компонент database engine можно создать план параллельных запросов. Если код или алгоритм использует больших объемов данных, убедитесь, что запрос, присвоенное `RxSqlServerData` оптимизирован для параллельного выполнения. Запрос, который не выполняется в рамках плана параллельного выполнения, может выполниться в одном процессе для вычисления.

Если необходимо работать с большими наборами данных, используйте среду Management Studio или другим анализатор запросов SQL, прежде чем выполнять код R, для анализа плана выполнения. Выполните все рекомендуемые действия для улучшения производительности запроса. Например, отсутствующий индекс таблицы может повлиять на время, затраченное на выполнение запроса. Дополнительные сведения см. в разделе [монитора и настройки производительности--... /.. / relational-databases/performance/monitor-and-tune-for-performance.md).

Другой распространенная ошибка, может повлиять на производительность заключается в том, что запрос получает больше столбцов, чем необходимо. Например если формула зависит только три столбца, но в исходной таблице есть столбцы, 30, перемещаются данные без необходимости.

 + Старайтесь не использовать `SELECT *`!
 + Внимательно просмотрите столбцы в наборе данных и выберите только те, необходимые для анализа
 + Удалить из запросов все столбцы, которые содержат типы данных, которые несовместимы с кода R, например идентификаторы GUID и идентификаторами rowguids
 + Проверьте форматы неподдерживаемые даты и времени
 + Вместо загрузки таблицы, создайте представление, которое выбирает определенные значения или приводит столбцы, чтобы избежать ошибок преобразования

**Оптимизация алгоритм машинного обучения**


Этот раздел содержит прочие советы и ресурсы, относящиеся к RevoScaleR и другие параметры в Microsoft R.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-r-package-management-for-sql-serverrr-package-management-for-sql-server-r-servicesmd"></a>7. &nbsp;[R пакета управления для SQL Server](r/r-package-management-for-sql-server-r-services.md)

*Обновлено: 2017 г-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 22.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2add5a7e1aef02487ac875e353c51161658050a4 5da92dd8b5402266a837172bda9aaabed3162ce8  (PR=2939  ,  Filename=r-package-management-for-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



В этом разделе описываются функции управления пакетами, которые можно использовать для управления пакетами R, запущенных на экземпляре SQL Server.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения служб

**Пакет управления с помощью T-SQL**


Можно установить пакеты R с правами администратора на компьютере, если у вас этих прав, и в том случае, если вы являетесь единственным лицом, использующим сервер для заданий машины обучения.

Тем не менее если требуется предоставлять другим пользователям пакетов, или если требуется несколько пользователей для запуска заданий обучения компьютера на сервере, является более эффективным библиотеку общих пакета. SQL Server поддерживает это посредством ролей базы данных.

Для установки ролей и добавление пользователей ролям отвечает администратор базы данных. Через роли Администратор базы данных можно контролировать, кто имеет разрешение на добавление и удаление пакетов R из среды SQL Server и можно проводить аудит установки пакета.

**Роли базы данных для пакета управления**


Следующие новые роли базы данных поддерживают безопасное установки и управления пакета R в SQL Server:

- `rpkgs-users`: Позволяет пользователям использовать любой общей пакеты, которые были установлены членами `rpkgs-shared` роли.

- `rpkgs-private`-Обеспечивает доступ к общей пакеты с теми же разрешениями, `rpkgs-users` роли. Члены этой роли также могут устанавливать, удалять и использовать пакеты, относящиеся к частной области.

-  `rpkgs-shared`-Обеспечивает те же разрешения, что `rpkgs-private` роли. Пользователи, являющиеся членами этой роли, также могут устанавливать и удалять общие пакеты.

- `db_owner`: Имеет те же разрешения, как `rpkgs-shared` роли. Кроме того, позволяет предоставить пользователям право на установку или удаление как общих, так и закрытых пакетов.

**Создание библиотеки внешнего пакета с помощью T-SQL**


Кроме того, 2017 г. SQL Server поддерживает инструкции T-SQL, **Создание ВНЕШНЕЙ БИБЛИОТЕКИ**, для поддержки управления внешние библиотеки, администратор базы данных. В настоящее время можно использовать эту инструкцию для создания библиотеки под управлением Windows для R. дополнительную поддержки запланировано в будущем пакеты Python, а также для пакетов, написанные для выполнения на других платформах, например в Linux.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>8. &nbsp;[Настройки обучения машины служб (в базе данных) для SQL Server](r/set-up-sql-server-r-services-in-database.md)

*Обновлено: 2017 г-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_7) | [Далее](#TitleNum_9))

<!-- Source markdown line 240.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 452dc36b4d0097f9562642238ba49eea0373d25b 4d355f6494b417dd90dce3943e7176eaece7336e  (PR=3070  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



Если создать решение R на клиентском компьютере обработки и анализа данных, необходимо запустить код с помощью имени компьютера SQL Server в контексте можно использовать встроенную проверку подлинности Windows или имени входа SQL.

* Для имен входа SQL: имя входа должно иметь соответствующие разрешения на доступ к базе данных, из которой будут считываться данные. Это можно сделать, добавив *подключиться к* и *ВЫБЕРИТЕ* разрешения, либо путем добавления имени входа *db_datareader* роли. Для имен входа, которые необходимо создать объекты, добавить *DDL_admin* права. Для имен входа, которые необходимо сохранить данные в таблицах, добавьте имя входа для *db_datawriter* роли.

* Для проверки подлинности Windows: может потребоваться настроить источник данных ODBC на клиенте обработки и анализа данных, который указывает имя экземпляра и другие сведения. Дополнительные сведения см. в разделе [администратор источников данных ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

**Дальнейшие действия**


После проверки того, что функциональные возможности выполнения скриптов работает в SQL Server, можно выполнить команды R и Python, в SQL Server Management Studio, Visual Studio Code или любым другим клиентом, можно отправить инструкции T-SQL на сервере.

Тем не менее может потребоваться внести некоторые изменения конфигурации системы для поддержки активно используется машинное обучение, или добавить новый R-пакеты.

В этом разделе перечислены некоторые общие изменения, вносимые для поддержки машинного обучения.

**Добавить больше рабочих учетных записей**


Если вы считаете, что можно активно использовать R или если ожидается, что несколько пользователей одновременно быть выполнение скриптов, можно увеличить количество рабочих учетных записей, назначенных для службы панели запуска. Дополнительные сведения см. в разделе [изменить пул учетных записей пользователей для SQL Server R Services--modify-the-user-account-pool-for-sql-server-r-services.md).

**<a name="bkmk_optimize"></a>Оптимизировать сервер для выполнения внешних скриптов**




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-sql-server-configuration-for-use-with-rrsql-server-configuration-r-servicesmd"></a>9. &nbsp;[Конфигурации SQL Server для использования с помощью R](r/sql-server-configuration-r-services.md)

*Обновлено: 2017 г-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_8) | [Далее](#TitleNum_10))

<!-- Source markdown line 149.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3f57bae70e3c118c1e2bcd57017322940bae83f8 f296242d470db47077cba4215ef420bd0c60bf33  (PR=2660  ,  Filename=sql-server-configuration-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



Если запрос возвращает один узел памяти (узел 0), либо не имеет оборудования NUMA, либо оборудование настроено как с чередованием (не NUMA). SQL Server также игнорирует оборудования NUMA при существует четыре или меньшее число процессоров или если по крайней мере на одном узле находится только один ЦП.

Если на компьютере установлено несколько процессоров, но не имеет оборудования NUMA, можно также использовать [программной архитектуры NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) для разделения процессоров на более мелкие группы.  В SQL Server 2016 и 2017 г. SQL Server компонент программной архитектуры NUMA включается автоматически при запуске службы SQL Server.

При программной архитектуры NUMA включена, SQL Server автоматически управляет узлов Тем не менее, чтобы оптимизировать для конкретных рабочих нагрузок, можно отключить _нежесткой привязке_ и вручную настроить сходство ЦП в узлы NUMA мягкой. Это поможет вам больше возможностей управления, по которому рабочих нагрузок назначены какие узлы, особенно в том случае, если используется выпуск SQL Server, который поддерживает управление ресурсами. Задание соответствия Процессоров и выравнивание пулов ресурсов с группами процессоров, можно уменьшить задержку и убедитесь, что связанные процессы выполняются в том же узле NUMA.

Общий процесс настройки программной архитектуры NUMA и процессоров для поддержки рабочих нагрузок R выглядит следующим образом:

1. Включить программной архитектуры NUMA, если он доступен
2. Определить соответствие процессоров
3. Создание пулов ресурсов для внешних процессов, с помощью [ресурсов регулятора--... /r/Resource-governance-for-r-Services.MD)
4. Назначения [групп рабочей нагрузки..-- /.. / relational-databases/resource-governor/resource-governor-workload-group.md) для конкретных Территориальные группы

Сведения, включая пример кода см. в этом учебнике: [SQL оптимизации советы и рекомендации (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Другие ресурсы:**



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-performance-tuning-for-r-in-sql-serverrsql-server-r-services-performance-tuningmd"></a>10. &nbsp;[Повышении производительности R в SQL Server](r/sql-server-r-services-performance-tuning.md)

*Обновлено: 2017 г-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_9) | [Далее](#TitleNum_11))

<!-- Source markdown line 76.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9c30753efdec81e499d5654b5b7a07f0cfe5b003 136a9f483bc8c9e1f69cf9d340d1472c21a52ec4  (PR=2565  ,  Filename=sql-server-r-services-performance-tuning.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



- Настройте экземпляр SQL Server для операций обработчика баланс базы данных и R или выполнения на должном уровне сценария Python. Это может быть изменение SQL Server по умолчанию для памяти и использования ЦП, NUMA и настройки соответствия процессоров и создание групп ресурсов.

- Оптимизация удаленного сервера для поддержки эффективного использования внешних скриптов. Увеличение числа учетных записей, используемых для выполнения внешних скриптов, включения управления пакетами, может включать и назначение пользователям связанных ролей безопасности.

- Применение конкретных оптимизации хранилища данных и передачи в SQL Server, включая индексирования и стратегии статистики, конструктор запросов и оптимизации запросов и структуру таблиц, используемых для машинного обучения. Также может анализировать источники данных и данных транспорта методов или изменения процессов ETL для оптимизации извлечения признаков.

- Настройки аналитической модели во избежание недостатки. Области оптимизации, которые возможны зависит от сложности кода R, пакеты и данные, которые вы используете. Основные задачи включают удаление преобразования данных много ресурсов или Разгрузка данных подготовки или компонент технических задач из R или Python процессов ETL или SQL. Может также рефакторинг скрипты, исключение устанавливает пакет в строке, разделить отдельные инструкции для обучения, оценки и оценки кода R и упростить код, чтобы работать более эффективно, как хранимую процедуру.

**Статьи в этой серии**


+ [Для R в SQL Server - оборудования — Настройка производительности... \r\sql-Server-Configuration-r-Services.MD)

    Содержит рекомендации по настройке оборудования,..! ДОБАВИТЬ NotShown--ssNoVersion_md--... \..\includes\ssnoversion-md.md)] устанавливается на, а также для настройки экземпляра SQL Server для лучшей поддержки внешних скриптов. Это особенно полезно для **администраторам баз данных**.

+ [Помощник по настройке производительности для R в SQL Server - оптимизация кода и данных--... \r\r-and-Data-Optimization-r-Services.MD)



&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-data-science-scenarios-and-solution-templatestutorialsdata-science-scenarios-and-solution-templatesmd"></a>11. &nbsp;[Сценарии обработки и анализа данных и шаблоны решений](tutorials/data-science-scenarios-and-solution-templates.md)

*Обновлено: 2017 г-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_10) | [Далее](#TitleNum_12))

<!-- Source markdown line 45.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 22c621731015f2192cb0b8d61b22062a4be50e70 6cf9e3f0a3803ed2bce9c4ffadfd7314f15f6b51  (PR=2964  ,  Filename=data-science-scenarios-and-solution-templates.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



[Предсказать, как и когда для связи с потенциальными клиентами](https://microsoft.github.io/r-server-campaign-optimization/)

**Что:** это решение использует insurance Отраслевые данные для прогнозирования на основе демографических данных, данные предыстории ответа и сведения о продукте интересов.  Рекомендации также создаются для указания наиболее канала и время пользователям подход для оказания влияния на поведение покупки.

**Как:** решение создает и сравниваются несколько моделей. Решение также демонстрирует автоматических интеграцию данных и Подготовка данных с помощью хранимых процедур. Параллельные приведены образцы для SQL Server в базе данных, в Azure, а HDInsight Spark.

**Здравоохранение: спрогнозировать время нахождения в больнице**


[Прогнозирование время нахождения в больницы](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Что:** точного прогнозирования пациентов, которые могут потребовать долгосрочной hospitalization является важной частью внимания и на планирование. Администраторы должны иметь возможность определить, какие средства требуется больше ресурсов и caregivers нужно гарантировать, что они могут соответствовать требованиям пациентов.

**Как:** это решение использует виртуальная машина анализа данных и включает экземпляр SQL Server с помощью машинного обучения включена. Он также включает набор отчетов Power BI, которые можно использовать для взаимодействия с развернутой модели.

**Обработка клиента**


[Шаблон прогнозирования обработка клиента (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**Что:** анализ и прогнозирование, обработка клиента — важный аспект любого отрасли, где необходимо обрабатываются и предотвратить потери клиентов конкурентам: банковских операций, связи и розничной торговли и др. Целью такого анализа является определение клиентов, которые с высокой вероятностью могут уйти к конкурентам, и принятие надлежащих мер для их удержания.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-whats-new-in-machine-learning-services-in-sql-serverwhat-s-new-in-sql-server-machine-learning-servicesmd"></a>12. &nbsp;[Новые возможности службы обучения машины в SQL Server](what-s-new-in-sql-server-machine-learning-services.md)

*Обновлено: 2017 г-08-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_11))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 025e68a93895a3788a63847cd91bff068775acf3 6dc0be2920c670235038a126d135e08d6f16ec3a  (PR=2712  ,  Filename=what-s-new-in-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=ea75391663eb4d509c10fb785fcf321558ff0b6e) -->



> Службы машины обучения, включая использование R или Python, в настоящее время не поддерживаются при запуске SQL Server в Linux или в базе данных Azure SQL. Поиск изменений в более поздней версии.
>
> Однако собственный оценки с помощью функции ПРОГНОЗИРОВАНИЯ в настоящее время поддерживается в выпуске Linux.

**Интеграция Python в базе данных**


Можно запустить Python в хранимых процедурах или Python удаленно с помощью имени компьютера SQL Server в контексте выполнения. Такая интеграция открывает новые пути для подавляющего сообщество Python ученые разработчиков и данных для использования возможностей SQL Server и для изучения принципиально новые функциональные возможности от корпорации Майкрософт, таких как **revoscalepy** и **microsoftml**.

Разработчиков SQL Server предоставляет доступ к обширные библиотеки Python экосистему с открытым исходным кодом, включая наиболее популярных платформ, таких как scikit-узнать Tensorflow, Caffe и Theano/Keras.

Но выполняется не в базе данных только для машинного обучения; Python Существует множество других возможных приложений для интеграции с SQL, используя преимущества соответствующих языков для доставки более разумно, мощные решения Python.

+ **revoscalepy**

    Этот выпуск включает окончательной версии **revoscalepy**, которые передают Pythonic эквиваленты масштабируемой, алгоритмы в RevoScaleR потоковой передачи. Можно создавать модели Python для линейной и логистической регрессии, деревья принятия решений, повышенных деревьев и случайные леса, все параллельно и способны выполнялась в контекстах удаленных вычислений.

    Дополнительные сведения см. в разделе [новые возможности revoscalepy--python или что является revoscalepy.md).

+ Контексты удаленных вычислений для Python

    Этот выпуск поддерживает использование нескольких источников данных и контекстах удаленных вычислений. Специалист по анализу данных или разработчик могут выполнять код Python на удаленный экземпляр SQL Server, для просмотра данных или моделей создаются без перемещения данных. Контексты удаленных вычислений для использования требуется **revoscalepy**.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в общедоступный репозиторий GitHub.com: [MicrosoftDocs, sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новый + обновленные (3 + 12): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (5 + 0): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (5 + 1): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (19 + 82): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (1 + 8): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (12 + 1): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 1): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (7 + 1): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (0 + 2): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (1 + 4): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (4 + 1): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (0 + 1): **средства для SQL** документы](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новый + обновленные (0 + 0): **Master Data Services (MDS) для SQL** документы](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



