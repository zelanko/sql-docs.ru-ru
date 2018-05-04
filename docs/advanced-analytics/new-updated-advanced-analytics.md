---
title: Обновить - Advanced Analytics для документации по SQL Server | Документы Microsoft
description: Отображение фрагментов обновленное содержимое для последних измененных в документации, Advanced Analytics в Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 04/28/2018
ms.openlocfilehash: bbce32579b54647e167c25d2708a80027ae0e678
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Новые и недавно обновленные: Advanced Analytics для SQL Server



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2018-02-03** &nbsp; - в - &nbsp; **2018-04-28**
- *Предметной области:* &nbsp; **Advanced Analytics для SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Установка SQL Server 2017 г. машинного самообучения, службы (в базе данных) в Windows](install/sql-machine-learning-services-windows-install.md)
2. [Установка SQL Server 2017 г машинного самообучения, Server (изолированный) в Windows](install/sql-machine-learning-standalone-windows-install.md)
3. [Компоненты SQL Server машины обучения из командной строки](install/sql-ml-component-commandline-install.md)
4. [Установка SQL Server машинного обучения компоненты без доступа к Интернету](install/sql-ml-component-install-without-internet-access.md)
5. [Установка служб R SQL Server 2016 (в базе данных)](install/sql-r-services-windows-install.md)
6. [Установка SQL Server 2016 R Server (изолированный)](install/sql-r-standalone-windows-install.md)
7. [Настройка Python клиентские средства для работы с SQL Server машинного обучения](python/setup-python-client-tools-sql.md)
8. [Использовать модель Python в SQL для обучения и оценки](tutorials/train-score-using-python-in-tsql.md)
9. [Поместите код Python в хранимой процедуре](tutorials/wrap-python-in-tsql-stored-procedure.md)
10. [Что такое службы машинного обучения SQL Server?](what-is-sql-server-machine-learning.md)
11. [Расширенные события для наблюдения за инструкциями PREDICT](xe-event-predict-tsql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Просмотр R и пакеты Python, установленные на сервере SQL Server](#TitleNum_1)
2. [Установить предварительно обученной машинного обучения моделей, основанных на SQL Server](#TitleNum_2)
3. [Настройка клиента обработки и анализа данных для разработки R на сервере SQL Server](#TitleNum_3)
4. [SQL Server машинного обучения и служб R (в базе данных)](#TitleNum_4)
5. [Выполнения Python, с помощью T-SQL](#TitleNum_5)
6. [Для создания модели с помощью Python с revoscalepy](#TitleNum_6)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-viewing-r-or-python-packages-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>1. &nbsp; [Просмотр R и пакеты Python, установленные на сервере SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Обновлено: 2018-04-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 208.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f ec6859ac91b27539dc36f21aec82c99937c0187a  (PR=5610  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f1f96a990644c0d6cfa5a1d88ccee959cab6c2b2) -->



**Python**


Этот пример возвращает список папок, включенных в Python `sys.path` переменной. Список содержит текущий каталог и путь к стандартной библиотеке.

```
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Результаты**

```
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Дополнительные сведения о переменной `sys.path` и он используется для задания пути поиска интерпретатора для модулей, в разделе [документации Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-install-pre-trained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>2. &nbsp; [Установить предварительно обученной машинного обучения моделей, основанных на SQL Server](r/install-pretrained-models-sql-server.md)

*Обновлено: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 140.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 aa03623d819750d4919feb7910b07ec1875bb509 7382228fa68b04b500a5fde73c29995e12aa20ac  (PR=5504  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



1. Запустите отдельного установщика Windows для любого [R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server) или [машины обучения Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Выберите языки, которые вы хотите обновить и выберите **Pre-trained моделей** параметр.

    > [!TIP]
    > Если вы ранее не выполнялась программа установки для обновления R Server (изолированный) и нужно добавить предварительно обученной модели, оставьте все ранее выбранные варианты **как**и выберите только что Pre **-обучения моделей** параметр . **Нет** снимите все выбранные ранее параметры; Если это сделать, программа установки удаляет компоненты.

    Рекомендуется принять параметры по умолчанию для расположений модели.

3. Нажмите кнопку **Продолжить**.

4. Примите все остальные, включая лицензионных соглашений.

После завершения установки необходимо выполнить некоторые дополнительные действия, чтобы зарегистрировать предварительно обученной модели.

1. Откройте командную строку Windows **администратор**.

2. Перейдите в папку установки начальной загрузки для R Server (изолированный), которая также содержит установщик Microsoft R.

3. Запустите `RSetup.exe` и указать компонент для установки, версии и к папке, содержащей исходные файлы модели, используя следующий синтаксис:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    Для параметра версии поддерживаются следующие значения:



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-set-up-a-data-science-client-for-r-development-on-sql-serverrset-up-a-data-science-clientmd"></a>3. &nbsp; [Настройка клиента обработки и анализа данных для разработки R на сервере SQL Server](r/set-up-a-data-science-client.md)

*Обновлено: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 39.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0583f8febcedc5dc2e14ca1a8073ca204ca37987 3d50ad8f35f2985944741a9b2211a461df2c13e4  (PR=5504  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



**Средства R**


Если вы устанавливаете R с SQL Server, вы получаете те же средства R, которые устанавливаются вместе с любой **базового** установки r, например RGui, Rterm и т. д. Поэтому с технической точки зрения, у вас все средства, необходимые для разработки и тестирования кода R.

Следующие стандартные средства R включены в *базовые установки* r и поэтому устанавливаются по умолчанию.

+ **RTerm**: терминал командной строки для выполнения скриптов R

+ **RGui.exe** — простой интерактивный редактор для R. Аргументы командной строки для RGui.exe и RTerm одни и те же.

+ **RScript** — средство командной строки для выполнения скриптов R в пакетном режиме.

Чтобы найти эти средства, определите R библиотеки, в которой была установлена при установке SQL Server или автономный машинного обучения функции. Например по умолчанию при установке средств R находятся в этих папках:

+ Службы SQL Server 2016 R: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Изолированный сервер Microsoft R: `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ Машины SQL Server 2017 г. изучение служб: `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Машинное обучение Server (изолированный): `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Если вам нужна помощь с помощью средств R, просто откройте **RGui**, нажмите кнопку **справки**, а затем выберите один из параметров

**Microsoft R Client**


Клиент Microsoft R можно бесплатно загрузить, предоставляющая доступ к пакетам RevoScaleR для целей разработки. Установка клиента R, можно создать решения R, которые могут выполняться во всех контекстах поддерживаемых вычислений, включая анализа в базе данных SQL Server и распределенных вычислений в Hadoop, Spark или Linux с помощью сервера обучения Machine R.

Если вы уже установили другой среды разработки R, например RStudio, не забудьте изменить параметры среды для использования библиотек и исполняемых файлов, предоставляемые Microsoft R клиента. В результате можно использовать все возможности пакета RevoScaleR, несмотря на то, что производительности будет ограничен.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sql-server-machine-learning-and-r-services-in-databasersql-server-r-servicesmd"></a>4. &nbsp; [SQL Server машинного обучения и служб R (в базе данных)](r/sql-server-r-services.md)

*Обновлено: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 83.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b1a95a7f6d391a518762eb271e8ea7e0d684d403 7fbfabf62917e03e2bcb99d297e1c9d0f0604440  (PR=5504  ,  Filename=sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



Выберите лучший язык для задачи. R лучше всего подходит для статистических вычислений, которые трудно реализовать с помощью SQL. Для операций на основе набора данных, использовать возможности *{включенные-Content-снизится-здесь}* для достижения максимальной производительности. Используете ядро базы данных в памяти для быстрого вычислений над столбцами.

**Шаг 4: Оптимизация решения**


Когда модель готова для масштабирования данных предприятия, специалист по анализу данных часто работает с SQL DBA или разработчику оптимизации процессов, таких как:

+ Формирование признаков
+ Приема данных и преобразование данных
+ Оценки

В большинстве случаев с помощью R специалисты по анализу данных имели проблем производительности и масштабирования, особенно при использовании больших наборов данных. Это так, как общая реализация среды выполнения является однопотоковым и может вместить только те наборы данных, которые помещаются в доступную память на локальном компьютере. Интеграция со службами SQl Server Machine Learning предоставляет множество функций, для повышения производительности, с большим объемом данных:

+ **RevoScaleR**: R этот пакет содержит реализации некоторых наиболее популярных функций R, переработанные для обеспечения параллелизма и масштабирования. Пакет также содержит функции, дополнительно повышающие производительность и масштабируемость за счет принудительной отправки вычислений *{включенные-Content-снизится-здесь}* компьютера, который обычно обладает гораздо большим объемом памяти и вычислительной мощностью.

+ **revoscalepy**. Эта библиотека Python, доступных в SQL Server 2017 г реализует наиболее популярных функций в RevoScaleR, например контекстах удаленных вычислений и многие алгоритмы, которые поддерживают распределенную обработку.

**Ресурсы**

+ [Практический пример использования производительности]
+ [R и оптимизация данных]

**Шаг 5: Развертывание и использование**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-run-python-using-t-sqltutorialsrun-python-using-t-sqlmd"></a>5. &nbsp; [Выполнения Python, с помощью T-SQL](tutorials/run-python-using-t-sql.md)

*Обновлено: 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 306.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bde8c6476df259d225847c08224cefd02f3529d5 cad56997abe7928b588ac4a0302384c5edc1ede5  (PR=5497  ,  Filename=run-python-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



2. Обратите внимание, что значения индекса не выводятся, даже если индекс используется для получения определенных значений из data.frame.

    **Результаты**

    |ResultValue|
    |------|
    |0,5|
    |2|

**Выходные значения в data.frame, использование индекса**


Давайте посмотрим, как работает преобразование data.frame с наших двух рядов, содержащий результаты простой математических операций. Первый имеет индекс последовательные значения, созданные Python. Вторая использует произвольный индекса строковых значений.

1. В этом примере возвращает значение из серии, использующий целочисленного индекса.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

Помните, что автоматически созданный индекс начинается с 0. Попробуйте использовать вне диапазона значения индекса и посмотрим, что произойдет.

2. Теперь давайте получают одно значение из других кадров данных с индексом строки.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

**Результаты**

|ResultValue|
|------|
|0,5|

Если вы попытаетесь использовать числовой индекс для получения значения из этой серии, возникает сообщение об ошибке.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>6. &nbsp; [Для создания модели с помощью Python с revoscalepy](tutorials/use-python-revoscalepy-to-create-model.md)

*Обновлено: 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_5))

<!-- Source markdown line 22.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5b642b391ca571412c30c8470875d3d4d3c57246 bd83387eb8a1076a1396bbd48dca12872843aa2f  (PR=5497  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



Если вы установили предварительную версию служб SQL Server 2017 г., следует обновить для по крайней мере RTM-версии. Чтобы развернуть и улучшения функций Python продолжалось более поздние версии службы. Некоторые возможности работы с этим учебником может не работать в ранних предварительных версий.

+ В этом примере используется стандартные среды Python, с именем `PYTEST_SQL_SERVER`. Среде был настроен для хранения **revoscalepy** и другие необходимые библиотеки.

    Если у вас среду с запуском Python, это необходимо сделать отдельно. Инструкции для создания или изменения среды Python находится вне области видимости для этого учебника. Дополнительные сведения о настройке клиента Python, который содержит нужные библиотеки см. в разделе [клиента Python установите](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) и [Python ссылки на средства](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

**Контексты удаленных вычислений и revoscalepy**


В этом примере демонстрируется процесс создания модели Python в удаленной _контекста вычислений_, позволяющее работает на клиентском компьютере, но выберите удаленной среде, например SQL Server, Spark или компьютере обучения, сервер, где фактически выполняются операции. Использование контекстов вычислений делает проще написать код, один раз и развернуть ее на любой поддерживаемый среде.

Для выполнения кода Python в SQL Server требуется **revoscalepy** пакета. Это специальный пакет Python, предоставленного корпорацией Майкрософт, аналогично **RevoScaleR** пакет языка R. **Revoscalepy** пакет поддерживает создание контекстов вычислений и предоставляет инфраструктуру для передачи данных и моделей между локальной рабочей станции и удаленном сервере. **Revoscalepy** функции, поддерживаемые выполнение кода в базе данных — [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новый + обновленные (11 + 6): &nbsp; &nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (18 + 0): &nbsp; &nbsp; **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (218 + 14): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (14 + 0): &nbsp; &nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (3 + 2): &nbsp; &nbsp; **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (3 + 3): &nbsp; &nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (7 + 10): &nbsp; &nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 3): &nbsp; &nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **средства для SQL** документы](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новый + обновленные (0 + 0): **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../samples/new-updated-samples.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)

