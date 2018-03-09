---
title: "Обновить - Advanced Analytics для документации по SQL Server | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации, Advanced Analytics в Microsoft SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 02/03/2018
ms.openlocfilehash: a40a991abe8f82b553ae621c24f9d4e81a92f8f6
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Новые и недавно обновленные: Advanced Analytics для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-12-03** &nbsp; - в - &nbsp; **2018-02-03**
- *Предметной области:* &nbsp; **Advanced Analytics для SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Установка новых пакетов Python в SQL Server](python/install-additional-python-packages-on-sql-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Известные проблемы в службах машин обучения](#TitleNum_1)
2. [Преобразование кода R для выполнения в базе данных](#TitleNum_2)
3. [Определить, какие пакеты R установлены на сервере SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp;[Известные проблемы в работе службы обучения машины](known-issues-for-sql-server-machine-learning-services.md)

*Обновлено: 2018-02-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 163.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c6f46adcf795c43f818120b88407a3a89304cb27 c781562605f5cd77f6c43bfe5e89810cb72ceae0  (PR=4789  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=386bfb688843bac7fa4d83dc1cfef94dd19db110) -->



Другие известные проблемы, которые могут повлиять на решения R см. в разделе [машины обучения Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) сайта.

**Отказано в доступе предупреждение при выполнении скриптов R на сервере SQL Server в расположении по умолчанию не**


Если экземпляр SQL Server был установлен в расположении не по умолчанию, такие как за пределами `Program Files` папку, предупреждение ACCESS_DENIED возникает при попытке запуска скриптов, которые устанавливают пакета. Например:

> *В normalizePath(path.expand(path) winslash, mustWork): путь [2] = «~ExternalLibraries/R/8/1»: Отказано в доступе*

Причина заключается в функцию R пытается считать путь что не выполняется, если встроенной группе пользователей **SQLRUserGroup**, не имеет доступа на чтение. Предупреждение, которое возникает не блокирует выполнение текущего сценария R, но предупреждение может повторяться несколько раз всякий раз, когда пользователь запускает любой другой сценарий R.

При установке SQL Server по умолчанию, эта ошибка возникает, так как все пользователи Windows разрешения на чтение `Program Files` папки.

Этой проблемы будут учтены в предстоящих выпусках. Чтобы избежать этого, представляет собой группу **SQLRUserGroup**, с доступом на чтение для всех родительских папок `ExternalLibraries`.

**Ошибка сериализации между старой и новой версий RevoScaleR**


При передаче модели с помощью сериализованный формат для удаленного экземпляра SQL Server может появиться ошибка:

> *Ошибка в memDecompress (данные, тип = распаковки) -3 memDecompress(2) внутренней ошибки.*

Эта ошибка возникает при сохранении модели, используя последнюю версию функция сериализации [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), но экземпляр SQL Server, где выполняется десериализация модели установлена более старая версия API-интерфейсов RevoScaleR из SQL Server 2017 г. с накопительным обновлением 2 или более ранней версии.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-converting-r-code-for-execution-in-databaserconverting-r-code-for-use-in-sql-servermd"></a>2. &nbsp;[Код R преобразование для выполнения в базе данных](r/converting-r-code-for-use-in-sql-server.md)

*Обновлено: 2018-01-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 136.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a1d156fac1af5813ef75965071686b177e2aede7 fc8beff0aa0d7ea298e493b90984875e81e9143e  (PR=4493  ,  Filename=converting-r-code-for-use-in-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f486d12078a45c87b0fcf52270b904ca7b0c7fc8) -->



**Пакет кода R в хранимой процедуре**

+ Если код является довольно простым, можно внедрить в определяемой пользователем функции T-SQL без изменений, как описано в этих примерах:

    + [Создайте функцию R, работающий в rxExec](r/../tutorials/deepdive-create-a-simple-simulation.md)
    + [С помощью T-SQL и R конструируются](r/../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Если код является более сложным, используйте пакет R **sqlrutils** для преобразования кода. Этот пакет предназначен для опытных пользователей R написать код, хорошо хранимой процедуры.

    Первым шагом является переписывать код и R в виде одной функции с четко определенных входных и выходных данных.

    Затем с помощью **sqlrutils** пакета входы и выходы в правильном формате. **Sqlrutils** пакета создается код завершения хранимой процедуры и также могут регистрировать хранимой процедуры в базе данных.

    Дополнительные сведения и примеры см. в разделе [SqlRUtils](r/../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).

**Интеграция с другими рабочими процессами**

+ Используйте средства T-SQL и процессов ETL. Выполните конструируются извлечения признаков и очистка данных как часть рабочие процессы данных заранее.

    При работе в выделенном среду разработки R, такие как средства R для Visual Studio или RStudio может извлечь данные на компьютере, последовательно, анализа данных и затем записи или отображения результатов.

    Тем не менее при переносе кода автономный R для SQL Server большая часть этого процесса может быть упрощена или делегировать с другими средствами SQL Server.

+ Используйте безопасный, асинхронный визуализации стратегии.

    Часто пользователи SQL Server нет доступа к файлам на сервере и клиентских средств SQL обычно не поддерживают R графического устройства. При создании диаграммы или другие графические как часть решения, рассмотрите возможность экспорта графики как двоичные данные и сохранение в таблице или записи.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp;[Определения R-пакетов, установленных на сервере SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Обновлено: 2018-01-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2))

<!-- Source markdown line 78.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9a065066398843a4bed318fa46d4982d712915a9 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f  (PR=4715  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=9e6a029456f4a8daddb396bc45d7874a43a47b45) -->




**Получить расположение библиотеки и версии**


Следующий пример возвращает расположение библиотеки в локальном контексте и версия пакета RevoScaleR.

```
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

**Определить путь к библиотеке, используемый сервером SQL Server**


Если вы обновили машинного обучения компонентов с помощью привязки, путь к библиотеке R может измениться. В этом случае предыдущих ярлыки средств R может ссылаться на более ранней версии. Чтобы версии путь и пакета, используемый сервером SQL Server, можно выполнить команду, подобную следующей:

```
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Результаты**

```
STDOUT message(s) from external script:
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Аналогичные статьи о новых или обновленных статьях

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметной области, *сделать* новыми или были недавно обновлены статьи


- [Новый + обновленные (1 + 3):&nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (0 + 1):&nbsp; **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 1):&nbsp; **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (0 + 1):&nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (12 + 1): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (6 + 2):&nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (15 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (2 + 9):&nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (1 + 0):&nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 1):&nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (1 + 1):&nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (0 + 1):&nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (1 + 2):&nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2):&nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметной области, которые выполняют *не* иметь любой новыми или были недавно обновлены статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../sample/new-updated-sample.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)


