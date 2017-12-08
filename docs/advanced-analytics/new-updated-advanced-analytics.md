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
ms.date: 12/02/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.openlocfilehash: 636e243f1f39f0bfa688c6caada1e03078de9a32
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Новые и недавно обновленные: Advanced Analytics для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-09-28** &nbsp; - в - &nbsp; **2017 г-12-02**
- *Предметной области:* &nbsp; **Advanced Analytics для SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Добавить SQLRUserGroup в качестве пользователя базы данных](r/add-sqlrusergroup-to-database.md)
2. [Как использовать функции RevoScaleR для поиска или установка пакетов R в SQL Server](r/use-revoscaler-to-manage-r-packages.md)
3. [Использование языка R в базе данных Azure SQL](r/using-r-in-azure-sql-database.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Известные проблемы в службах машин обучения](#TitleNum_1)
2. [Создание локального репозитория пакетов с помощью miniCRAN](#TitleNum_2)
3. [Определить, какие пакеты R установлены на сервере SQL Server](#TitleNum_3)
4. [Установка дополнительных пакетов R в SQL Server](#TitleNum_4)
5. [Установка SQL Server машинного обучения функции на виртуальной машине Azure](#TitleNum_5)
6. [Установить предварительно обученные машинного обучения моделей, основанных на SQL Server](#TitleNum_6)
7. [Чтобы избежать ошибок в R-пакеты, установленные в библиотек пользователей](#TitleNum_7)
8. [Подготовьте виртуальную машину для машинного обучения в Azure](#TitleNum_8)
9. [RevoScaleR](#TitleNum_9)
10. [Включить или отключить управление пакет R для SQL Server](#TitleNum_10)
11. [Настройка клиента обработки и анализа данных для использования с SQL Server](#TitleNum_11)
12. [Настройка служб машинного обучения SQL Server (в базе данных)](#TitleNum_12)
13. [Автоматически устанавливать службы обучения машины (в базе данных)](#TitleNum_13)
14. [Шаг 3. Анализ и визуализация данных](#TitleNum_14)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp;[Известные проблемы в работе службы обучения машины](known-issues-for-sql-server-machine-learning-services.md)

*Обновлено: 2017 г-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 321.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00121c648c21576d5c86494137de1d4d81e2e265 c65973f6ae9253af5ecc621916ef36d7c0398789  (PR=3980  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



**Выполнение кода Python или Python проблемы пакетов**


В этом разделе содержатся известные проблемы, относящиеся к ОС Python SQL Server, а также проблемы, связанные с пакетами Python, опубликованные корпорацией Майкрософт, включая [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

**Вызов предварительно обученные модели завершается неудачей, если указан слишком длинный путь к модели**


При установке предварительно обученные модели в установке по умолчанию, в зависимости от того, имя компьютера и имя экземпляра, полученный полный путь к файлу обученной модели может быть слишком длинное для Python для чтения. Это ограничение будет исправлено в будущих службы.

Существует несколько обходные решения:

+ При установке предварительно обученные модели, выберите пользовательское расположение.
+ Если это возможно Установка экземпляра SQL Server в разделе пользовательский путь установки, например C:\SQL\MSSQL14. MSSQLSERVER.
+ Используйте служебную программу Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) Чтобы создать жесткую связь, сопоставляется модели файла более короткий путь.

**Не удалось инициализировать переменную varbinary приводит к ошибке в BxlServer**


При выполнении кода Python в SQL Server с помощью `sp_execute_external_script`и код есть выходные данные переменных типа varbinary(max), varchar(max) или подобных типов, переменной, необходимо инициализировать или как часть сценария. В противном случае компонент данных exchange, BxlServer, вызывает ошибку и прекращает работу.

Это ограничение будет исправлено в будущих службы. Избежать этого убедитесь, что переменная инициализируется в сценарий Python. Можно использовать любое допустимое значение, как показано в следующих примерах:

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-create-a-local-package-repository-using-minicranrcreate-a-local-package-repository-using-minicranmd"></a>2. &nbsp;[Создать репозиторий локального пакета с помощью miniCRAN](r/create-a-local-package-repository-using-minicran.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 43.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 44b77cb127e9ffab1777216a66f0e5be9c82f3d2 65e30f10fc36acb3ce95f60f51f3501fbc98ad08  (PR=4150  ,  Filename=create-a-local-package-repository-using-minicran.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



-   **Процесс установки в автономном режиме**: для установки пакета для отключения сервера требует также загрузить все зависимости пакета, с помощью miniCRAN упрощает получение всех зависимостей в правильном формате.

-   **Улучшенное управление версиями**: В многопользовательской среде есть достаточные основания для того чтобы избежать неограниченный установки нескольких версий пакета на сервере.

После создания репозитория, его можно изменить, добавив новые пакеты или обновления версии существующих пакетов.

**Шаг 1. Установите пакет miniCRAN**


Начните с создания репозитория miniCRAN для использования в качестве источника. На компьютере, который имеет доступ к Интернету, необходимо создать этот репозиторий.

1.  Установка пакета miniCRAN и необходимая **igraph** пакета.

```
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
```

**Шаг 2. Определить источник пакета: CRAN зеркала или моментальный снимок MRAN**


1. Указываете зеркальный сайт для использования в получении пакетов.

```
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
```

2.  Укажите локальную папку, в которой хранятся собранные пакеты. Не имя miniCRAN папки; Это может быть более описательное имя, например «GeneticsPackages» или «ClientRPackages1.0.2».

    Убедитесь создать папку заранее. Если возникает ошибка `local_repo` папка не существует, при выполнении кода R в более поздней версии.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp;[Определения R-пакетов, установленных на сервере SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 13d93acedc6e6b4615f1a244a2a1542910feb69e 9a065066398843a4bed318fa46d4982d712915a9  (PR=4150  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



+ Если найти пакет, сообщение, возвращенное должны выглядеть как «Команд выполнена успешно».

+ Если найти или загрузить пакет невозможно, возникает сообщение об ошибке, следующим образом: «произошла ошибка во внешнем сценарии: ошибка в library("RevoScaleR"): не найден пакет называется RevoScaleR»

**Получение списка установленных пакетов с помощью R**


Существует несколько способов получить список установленных или загруженных пакетов с помощью средств и функций R. Многие инструменты разработки R предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область R.

+ Из локальной программу R, используйте базовая функция R, например `installed.packages()`, который входит в `utils` пакета. Чтобы получить список, который является точным для экземпляра, необходимо явно указать путь к библиотеке или использовать средства R, связанных с библиотекой экземпляра.

+ Чтобы проверить пакет в контексте конкретного вычислений, можно использовать следующие функции из пакета RevoScaleR. Эти функции помогают идентифицировать пакетов в контексте указанной вычислений:

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage);

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages).

Например выполните следующий код R для получения списка пакетов, доступных в заданном контексте вычислений SQL Server.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```
**См. также:**




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-install-additional-r-packages-on-sql-serverrinstall-additional-r-packages-on-sql-servermd"></a>4. &nbsp;[Установка дополнительных пакетов R в SQL Server](r/install-additional-r-packages-on-sql-server.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 266.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ba48f1838857d90d6692aafc48f393777ac602fa 37de2586a344a99969bcd9a20723c021db2604a4  (PR=4150  ,  Filename=install-additional-r-packages-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Этот раздел содержит различные советы и образцы кода, связанные с установкой пакета R на сервере SQL Server.

**<a name="packageVersion"></a>Получите правильный пакет версии и формат**


Существует несколько источников R-пакетов, самые известные — CRAN и Bioconductor. На официальном сайте для языка R (<https://www.r-project.org/>) перечислены многие такие ресурсы. Многие пакеты публикуются на портале GitHub, где можно получить исходный код. Тем не менее вам могут предоставить R-пакеты, разработанные в вашей компании.

Независимо от источника необходимо убедиться, что пакет, который вы хотите установить имеет двоичный формат для платформы Windows. В противном случае загруженного пакета нельзя запускать в среде SQL Server.

Перед загрузкой, необходимо также проверить, совместим ли пакет в версии R, который работает в SQL Server.

**<a name="bkmk_zipPreparation"></a>Загрузить пакет как ZIP-файл**


Для установки на сервере без доступа к Интернету Загрузите копию пакета в формате ZIP-файл для установки в автономном режиме. Не распаковать пакет.

Например, следующая процедура описывает, чтобы получить правильную версию [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) пакет с сайта Bioconductor, при условии, что у компьютера есть доступ к Интернету.

1.  В списке **Package Archives** (Архивы пакетов) найдите версию **Windows binary** (Двоичный файл Windows).

2.  Щелкните правой кнопкой мыши ссылку. ZIP-файл и выберите **сохранить объект как**.

3.  Перейдите к локальной папке, где хранятся ZIP-пакеты и нажмите кнопку **Сохранить**.

Будет создана локальная копия пакета. Затем можно установить пакет или скопировать ZIP-пакет на сервер, который не имеет доступа к Интернету.

Дополнительные сведения о содержимом ZIP-архива и создании R-пакет, мы рекомендуем учебником, который можно загрузить в формате PDF в сайте проекта r.: [создания пакетов R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-installing-sql-server-machine-learning-features-on-an-azure-virtual-machinerinstalling-sql-server-r-services-on-an-azure-virtual-machinemd"></a>5. &nbsp;[Установки SQL Server машинного обучения функции на виртуальной машине Azure](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f4d287044b8bfda2dbe77fbf65b0d9cdd8f2ff42 2a8e33de6383f5d3af52256c5dfcb60184659eb8  (PR=4150  ,  Filename=installing-sql-server-r-services-on-an-azure-virtual-machine.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



6. Если вы планируете подключиться к экземпляру из клиента обработки и анализа удаленных данных, выполните [Дополнительные шаги--#additional этапы) при необходимости.

**Отключение функции обучения компьютера на виртуальной Машине SQL Server**


Также можно включить или отключить эту функцию на существующей виртуальной машины SQL Server в любое время.

1. Откройте колонку виртуальной машины.
2. Щелкните **Параметры**, а затем выберите **Конфигурация SQL Server**.
3. Внесите изменения в функциях и применить.

**<a name="existing"></a>Добавление существующей виртуальной Машине SQL Server 2016 Enterprise служб R**


При создании виртуальной машины Azure, включенные SQL Server без машинного обучения, можно добавить функцию, выполните следующие действия:

1. Повторно запустите..! ДОБАВИТЬ NotShown--ssNoVersion--... /.. /includes/ssNoVersion-MD.MD)] установки и добавьте компонент в **конфигурации сервера** странице мастера.
2. Разрешить выполнение внешних скриптов и перезапустите..! ДОБАВИТЬ NotShown--ssNoVersion--... /.. экземпляр /includes/ssNoVersion-MD.md]). Дополнительные сведения см. в разделе [задайте копии SQL Server R Services--... /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Необязательно.) Настройте доступ к базе данных для рабочих учетных записей R, если требуется удаленное выполнение скрипта.
   Дополнительные сведения см. в разделе [задайте копии SQL Server R службы--.. /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Необязательно.) Измените правило брандмауэра на виртуальной машине Azure, если вы планируете разрешить выполнение скрипта R из удаленных клиентов для обработки и анализа данных. Дополнительные сведения см. в разделе [Unblock брандмауэра--#firewall).
4. Установите или включите необходимые сетевые библиотеки. Дополнительные сведения см. в разделе [Добавить сетевых протоколов--#network).



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-install-pretrained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>6. &nbsp;[Установки обученная моделей машинного обучения на сервере SQL Server](r/install-pretrained-models-sql-server.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 96.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07b51584a90568cccceea382c44155e40e09c967 db083f8536fbb2ea5886fed787872867b5de5750  (PR=4150  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    For example, to enable use of the latest version of the pretrained models for Python, in a default instance of SQL Server 2017, you would run this statement:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    On a named instance, the command would be something like this:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Чтобы использовать Python обученная моделей с машины обучения Server (изолированный):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Например при условии, что установки по умолчанию машины обучения Server (автономный) с помощью программы установки SQL Server 2017 г., выполните следующую инструкцию:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. Для параметра версии поддерживаются следующие значения:



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-avoiding-errors-on-r-packages-installed-in-user-librariesrpackages-installed-in-user-librariesmd"></a>7. &nbsp;[Чтобы избежать ошибок в R-пакеты, установленные в библиотек пользователей](r/packages-installed-in-user-libraries.md)

*Обновлено: 2017 г-10-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 52cb9a53d7d9c31ee9bc6977464ebd2a18081ff3 3537aa6755c66f12c19bb3448dc9b5c8abb9cc28  (PR=3619  ,  Filename=packages-installed-in-user-libraries.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=aecf422ca2289b2a417147eb402921bb8530d969) -->



Однако это не сможет работать при запуске решения R в SQL Server, так как пакеты R должна быть установлена на конкретные стандартные библиотеки, связанный с экземпляром.

В противном случае при попытке вызова пакета может появиться следующая ошибка:

*Ошибка в library(xxx): не найден пакет называется «имя пакета»*

Рекомендуется также неправильный разработки установить необходимые пакеты R в библиотеку пользовательского как может привести к ошибкам при запуске решения другим пользователем, который не имеет доступа к расположение библиотеки.

**Установка пакетов R в библиотеку доступен**


**Для SQL Server 2016**

Используйте библиотеку пакет, связанный с экземпляром. Дополнительные сведения см. в разделе [R пакеты, установленные с SQL Server--installing-and-managing-r-packages.md)

**Для SQL Server 2017 г.**

SQL Server предоставляет возможности для управления несколькими версиями пакета и предоставить пользователям разрешения на отдельные пакеты без необходимости, что пользователи имеют доступ к файловой системе.

Дополнительные сведения о том, как создать библиотеку пакета shared и назначать пользователей ролям в разделе [R управление пакетами для SQL Server--r-package-management-for-sql-server-r-services.md.)




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-provision-a-virtual-machine-for-machine-learning-on-azurerprovision-the-r-server-only-sql-server-2016-enterprise-vm-on-azuremd"></a>8. &nbsp;[Подготовки виртуальной машины для машинного обучения в Azure](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

*Обновлено: 2017 г-10-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_7) | [Далее](#TitleNum_9))

<!-- Source markdown line 132.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 16439b4a8f5f4218edfcd746ed20ccbc8263dabc 1b3a8a7d1ceceaa459b3fd5640da26859df8d80b  (PR=3748  ,  Filename=provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=262e3cf5df2448bb6b532c0549c3d72daefe5a96) -->



|Имя| Комментарии|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 Enterprise с пакетом обновления 1 для Windows|Службы R для интеграции расширенной аналитики.|
|BYOL SQL Server 2016 SP1 Enterprise на Windows Server |Службы R для интеграции расширенной аналитики. |
|Бесплатная лицензия: SQL Server 2016 Developer с пакетом обновления 1 на Windows Server 2016 |Службы R для интеграции расширенной аналитики. |
| Виртуальная машина анализа данных — Windows 2012|Содержит популярных средств для обработки и анализа данных, включая Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, распространения Anaconda Python, Юлия профессионального выпуска developer и записные книжки Jupyter для R.|
| Виртуальная машина анализа данных — Windows 2016|Включает SQL Server 2016 Developer Edition с поддержкой аналитика R в базе данных.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 г предприятия Windows Server 2016| Службы обучения компьютера с поддержкой языка Python и R.|
|BYOL SQL Server 2017 г предприятия Windows Server 2016|Службы обучения компьютера с поддержкой языка Python и R.|
| Лицензия свободного SQL Server: SQL Server 2017 г Developer на Windows Server|Службы обучения компьютера с поддержкой языка Python и R.|
| **Другое**| *** |
| Машинного обучения сервера только SQL Server 2017 г Enterprise|Аналогично образа SQL Server 2016 Enterprise, но содержит автономной версии сервера Machine обучения и имеет ядро ScaleR, и функциональные возможности ввода в эксплуатацию оптимизирован для Windows сред.|
| Сервер машинного обучения для Windows|Содержит автономной версии сервера Machine обучения, с функциями ввода в эксплуатацию, оптимизированный для среды Windows.|



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-revoscalerrrevoscaler-overviewmd"></a>9. &nbsp;[RevoScaleR](r/revoscaler-overview.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_8) | [Далее](#TitleNum_10))

<!-- Source markdown line 18.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 92f2dfa2e75037a932415881c55d2fd37fc6847a c6e9f17f2df82447b18beff41769ae3ebfbed562  (PR=4150  ,  Filename=revoscaler-overview.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->




RevoScaleR — это пакет машины обучения функций, предоставляемых корпорацией Майкрософт, которая поддерживает обработки и анализа данных в масштабе.

+ Функции поддерживают импорт данных, преобразования данных, формирования сводных данных, визуализации и анализа.

+ _В масштабе_ означает, что операции можно выполняются для очень больших наборов данных, в параллельном режиме и на распределенных файловых систем. Алгоритмы работают над наборами данных, которые не помещаются в памяти, с помощью фрагментации и дизассемблировать результатов после выполнения операции.

+ RevoScaleR обеспечивает множество улучшений функций R с открытым кодом. Существует соответствующий базовый наиболее популярных функций R функции RevoScaleR. Функции RevoScaleR, обозначаются знаком **rx** или **Rx** префикс, чтобы облегчить их идентификацию.

+ RevoScaleR служит в качестве платформы для обработки и анализа данных. Например, можно использовать контексты вычислений RevoScaleR и преобразования с алгоритмами состояние рисунка в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Можно также использовать [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) для выполнения базовых функций R в параллельном режиме.

Примеры RevoScaleR в действии см. в этих блогах:

+ [Построение и развертывание прогнозную модель с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Один миллион прогнозы с машины обучения сервера в секунду](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Прогнозирование с помощью MicrosoftML советы такси](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Оптимизация производительности с rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

**Как получить RevoScaleR**




&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-enable-or-disable-r-package-management-for-sql-serverrr-package-how-to-enable-or-disablemd"></a>10. &nbsp;[Включить или отключить управление пакет R для SQL Server](r/r-package-how-to-enable-or-disable.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_9) | [Далее](#TitleNum_11))

<!-- Source markdown line 60.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f846cd7d601459a95e694ada41e9fc5285f3de9 83a4a84adf47670c7fd4599f889f27ec3c219708  (PR=4150  ,  Filename=r-package-how-to-enable-or-disable.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    If you do not specify a user, the current security context is used.

3. Выполните команду для каждой базы данных, где необходимо установить пакеты.

4.  Чтобы убедиться, что новые роли были успешно созданы, в SQL Server Management Studio выберите базу данных, разверните узел **безопасности**и разверните **ролей базы данных**.

    Можно также выполнить запрос к sys.database_principals из следующего:

```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,
        pr.authentication_type_desc, pe.state_desc,
        pe.permission_name, s.name + '.' + o.name AS ObjectName
    FROM sys.database_principals AS pr
    JOIN sys.database_permissions AS pe
        ON pe.grantee_principal_id = pr.principal_id
    JOIN sys.objects AS o
        ON pe.major_id = o.object_id
    JOIN sys.schemas AS s
        ON o.schema_id = s.schema_id;
```

4.  После включения функции можно использовать любой пользователь с соответствующими разрешениями [создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкции T-SQL для добавления пакетов. Пример того, как это работает см. в разделе [Установка дополнительных пакетов в SQL Server](r/install-additional-r-packages-on-sql-server.md).

**<a name="bkmk_disable"></a>Отключить управление пакетами**




&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-set-up-a-data-science-client-for-use-with-sql-serverrset-up-a-data-science-clientmd"></a>11. &nbsp;[Настройка клиента обработки и анализа данных для использования с SQL Server](r/set-up-a-data-science-client.md)

*Обновлено: 2017 г-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_10) | [Далее](#TitleNum_12))

<!-- Source markdown line 52.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f674f5d329211e4c7d8dc464bd70f1cdef633350 8c65fc96c04f32d1e4777870774a11f9fd2ee219  (PR=3765  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



    For setup information, see [How to install R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

    To configure RTVS to use your Microsoft R client libraries, see [About Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017 г.

    Даже бесплатный выпуск Community Edition включает в себя нагрузки обработки и анализа данных, что установка шаблонов проектирования для R, Python и F #.

    Загрузите Visual Studio из [этот сайт](https://www.visualstudio.com/vs/).

+ RStudio

    Если вы предпочитаете RStudio, для использования библиотек RevoScaleR вам потребуется выполнить некоторые дополнительные действия.

    - Установка клиента Microsoft R для получения необходимых пакетов и библиотек.
    - Обновите путь к R для использования среды выполнения Microsoft R.

    Дополнительные сведения см. в разделе [клиента R - настроить интерфейс IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

**Настроить интерфейс IDE**


+ cредства R для Visual Studio

    В разделе [этот сайт](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) некоторые примеры того, как создать и отладить R проектов, с помощью средства R для Visual Studio.

+ Visual Studio 2017 г.

    Если установить клиент Microsoft R или R Server **перед** установки Visual Studio, библиотеки R Server автоматически обнаруживаются и используется для пути к библиотеке. Если вы не установили библиотеки RevoScaleR из **средств R** последовательно выберите пункты **установить клиент R**.

**Выполнение R в SQL Server**


В этом примере использует Visual Studio 2017 г Community Edition с установлен рабочей нагрузки обработки и анализа данных.

1. Из **файл** последовательно выберите пункты **New** , а затем выберите **проекта**.

2. -Рука область содержит список предустановленных шаблонов. Нажмите кнопку **R**и выберите **проект R**. В **имя** введите `dbtest` и нажмите кнопку **ОК**.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>12. &nbsp;[Настройки обучения машины служб (в базе данных) для SQL Server](r/set-up-sql-server-r-services-in-database.md)

*Обновлено: 2017 г-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_11) | [Далее](#TitleNum_13))

<!-- Source markdown line 111.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4d355f6494b417dd90dce3943e7176eaece7336e 20bddb8ffd4cf3774b812a7376c70b95ccc57e92  (PR=3980  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



   + Службы ядра СУБД
   + Службы R Services (в базе данных)

7. После завершения установки перезагрузите компьютер.


**<a name="bkmk2017top"></a>Установка служб SQL Server 2017 г машинного обучения (в базе данных)**


> [!div class="checklist"]
> * Установка компонента database engine и машинного обучения функции
> * Необходимые действия после установки: включить машинного обучения и перезапустить
> * Дополнительные шаги после установки: Добавление правил брандмауэра, добавить пользователей, изменить или настроить учетные записи служб, Настройка клиента обработки и анализа удаленных данных.

**Начало работы**

1. Запустите..! ДОБАВИТЬ NotShown--ssNoVersion--... /.. Настройка /includes/ssNoVersion-MD.md]).

2. На **установки** выберите **автономная установка нового SQL Server или добавление компонентов к существующей установке**.

     ! [Установка службы обучения машины (In-Database)--media/2017setup-installation-page-mlsvcs.png «Запустите установку ядра базы данных с компьютера службы обучения»)

3. На **Выбор компонентов** выберите следующие параметры:

    + Выберите **службы компонента Database Engine**. Компонент database engine требуется в каждом экземпляре, с применением машинного обучения.

    + Выберите **машинного обучения службы (в базе данных)**. Этот параметр устанавливает поддержку для использования в базе данных R. После выбора этого параметра можно выбрать машинного обучения языка. Можно выбрать только R, или можно добавить R и Python.

    ! [Компонент службы обучения машины selection--media/2017setup-features-page-mls-rpy.png» выберите эти компоненты для R службы в базе данных»)

    Если параметры языка Python или R не выбран, мастер установки установит только структуре расширяемости, включающий запуска доверенные SQL Server и не устанавливает какие-либо компоненты конкретного языка.  Обычно рекомендуется начинать с установить хотя бы один язык. Однако могут использовать этот параметр, если планируется сразу же использовать процесс привязки для обновления машинного обучения компонентов. Дополнительные сведения см. в разделе [SqlBindR используется для обновления экземпляра R Services--use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



&nbsp;

&nbsp;

---

<a name="TitleNum_13"/>

### <a name="13-nbsp-unattended-installation-of-machine-learning-services-in-databaserunattended-installs-of-sql-server-r-servicesmd"></a>13. &nbsp;[Автоматической установки службы обучения машины (в базе данных)](r/unattended-installs-of-sql-server-r-services.md)

*Обновлено: 2017 г-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_12) | [Далее](#TitleNum_14))

<!-- Source markdown line 75.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ad203c90adff3f515b5f16472fad9753be7a421d 6925a9276bcd4a80babc7504de50400f1a5a2940  (PR=3765  ,  Filename=unattended-installs-of-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



В следующем примере показано, что аргументы, необходимые для выполнения автоматической автоматической установки служб SQL Server 2017 г машины (в базе данных) с помощью языка Python добавлен.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Обратите внимание, флаги, необходимые для Python в SQL Server 2017 г.:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

**Установить в именованном экземпляре R и Python**


В следующем примере показано, что аргументы, необходимые для выполнения автоматические, автоматической установки служб SQL Server 2017 г машины (в базе данных) на именованном экземпляре. Добавляются языков R и Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

**<a name="OldInstall"></a>Установка из командной строки для SQL Server 2016**


В следующем примере показано, что аргументы, необходимые для выполнения автоматические, автоматической установки SQL Server 2016 с помощью языка r. добавлен.



&nbsp;

&nbsp;

---

<a name="TitleNum_14"/>

### <a name="14-nbsp-step-3-explore-and-visualize-the-datatutorialssqldev-py3-explore-and-visualize-the-datamd"></a>14. &nbsp;[Step 3: анализ и визуализация данных](tutorials/sqldev-py3-explore-and-visualize-the-data.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_13))

<!-- Source markdown line 66.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 47edcfbd8da7cf1ea1ad03a05f86d3cd26014827 674a7c7d0e8290fc91970ed2aeda3b97d5165d75  (PR=4150  ,  Filename=sqldev-py3-explore-and-visualize-the-data.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    Class 4: `tip_amount` > $20

**Создание диаграммы с помощью Python в T-SQL**


Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поскольку визуализация таких мощное средство для понимания распределения данных и выбросов, Python предоставляет многие пакеты для визуализации данных. **Matplotlib** модуль является одним из более популярных библиотек для визуализации и имеется множество функций для создания гистограммы, точечных диаграмм, графиков поле и других диаграммах исследования данных.

В этом разделе вы узнаете, как работать с графики с помощью хранимых процедур. А чем открыть изображение на сервере, сохранения объекта Python `plot` как **varbinary** данных, а затем написать, что в файле, можно будет совместно или просмотреть в другом месте.

**Создать диаграмму как данные типа varbinary**


**Revoscalepy** модуля, входящий в состав служб SQL Server 2017 г машины обучения поддерживает функции, аналогичные доступным в **RevoScaleR** пакета для R.  В этом примере используется эквивалент Python `rxHistogram` строится на основе данных из гистограммы..! ДОБАВИТЬ NotShown--tsql... /.. запрос /includes/tsql-MD.md]).

Хранимая процедура возвращает сериализованный Python `figure` объект как поток **varbinary** данных. Двоичные данные нельзя просматривать непосредственно, но можно использовать код Python на стороне клиента для десериализации и просматривать данные и затем сохраните файл изображения на клиентском компьютере.

1. Создайте хранимую процедуру _SerializePlots_, если сценарий PowerShell это уже не сделано.

    - Переменная `@query` определяет текст запроса `SELECT tipped FROM nyctaxi_sample`, который передается блоку кода Python в качестве аргумента для входной переменной сценария `@input_data_1`.
    - Сценарий Python очень прост: **matplotlib** `figure` объектов используются для создания гистограмме и точечной диаграмме, и эти объекты сериализуются с помощью `pickle` библиотеки.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новый + обновленные (3 + 14): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (1+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (87 + 0): **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (5 + 4): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (0 + 1): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (2 + 2): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (10 + 9): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (2 + 4): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (4 + 2): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (0 + 1): **образцы для SQL** документы](../sample/new-updated-sample.md)
- [Новый + обновленные (21 + 0): **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (5 + 1): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (1 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новый + обновленные (0 + 0): **данных миграции Assistant (DMA) для SQL** документы](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


