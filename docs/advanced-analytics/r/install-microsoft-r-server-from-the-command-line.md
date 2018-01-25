---
title: "Установка сервера обучения Machine (автономный) или Microsoft R Server (изолированный) из командной строки | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 35194b08e43c98985e0ae0d03f1e470fe8370383
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="install-machine-learning-server-standalone-or-microsoft-r-server-standalone-from-the-command-line"></a>Установка сервера обучения Machine (автономный) или Microsoft R Server (изолированный) из командной строки

В этой статье описывается, как использовать аргументы командной строки SQL Server для установки следующих компонентов SQL Server с помощью командной строки:

+ [Машинного обучения Server (изолированный) в SQL Server 2017 г.](#bkmk_mls2017) 
+ [Microsoft R Server (изолированный), в SQL Server 2016](#bkmk_mrs2016)

**Автоматической** установки необходимо указать расположение программы установки и использовать аргументы, чтобы указать, какие функции нужно установить.

Для **тихой** установки укажите те же самые аргументы, добавив параметр **/q** . Предоставляются без вывода сообщений и не требуется никакого взаимодействия. Тем не менее программа установки завершается ошибкой, если требуемые аргументы были пропущены.

## <a name="prerequisites"></a>предварительные требования

Вам следует знать, как для выполнения командной строки установки SQL Server и иметь навыки работы с сценариев аргументов.

Дополнительные сведения см. в разделе [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).

При установке сервера Machine Learning или Microsoft R Server (изолированный) на компьютере, который имеет доступ к Интернету отсутствует, необходимо заранее загрузить необходимые компоненты R (или Python) и скопируйте их в локальную папку. Расположения загрузки. в разделе [Установка компонентов обучения компьютер без доступа к Интернету](installing-ml-components-without-internet-access.md).


## <a name="bkmk_mls2017"></a>Установка Microsoft машинного обучения Server (изолированный)

**Применяется к: SQL Server 2017 г.**

Выполните следующую команду из командной строки с повышенными привилегиями для установки только машины обучения Server (изолированный) и его обязательные компоненты.

+ Аргумент функции не требуется, — условия лицензии SQL Server.
+ Можно установить один язык, или R и Python, но требуется отдельная лицензия для каждого.

В этом примере показаны аргументы, используемые для установки R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

В этом примере показаны аргументы, используемые для установки Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MPY  /IACCEPTPYTHONOPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

+ Чтобы просмотреть ход выполнения и запросы, удалите аргумент _/q_.
+ При использовании аргумента **функции = SQL_SHARED_MR**, только машины обучения серверные компоненты устанавливаются вместе с Python ни R. Эта установка включает все необходимые компоненты, которые автоматически устанавливаются по умолчанию. Тем не менее рекомендуется добавить хотя бы один язык при установке в первый раз.
+ Добавить **SQL_INST_MR** установке поддержки для R.
+ Добавить **SQL_INST_MPY** поддержка Python.
+ **IACCEPTROPENLICENSETERMS** указывает, что вы приняли условия лицензионного соглашения для использования компонентов R с открытым исходным кодом.
+ **IACCEPTPYTHONLICENSETERMS** указывает вы приняли условия лицензионного соглашения по использованию компонентов Python.
+ **IACCEPTSQLSERVERLICENSETERMS** требуется для запуска мастера установки.


## <a name="bkmk_mrs2016"></a> Установка изолированного сервера Microsoft R Server

**Применяется к: SQL Server 2016**

Выполните следующую команду из командной строки с повышенными привилегиями для установки **только** Microsoft R Server (изолированный) и его обязательные компоненты. 

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

> [!TIP]
> Мы рекомендуем не установить это на том же компьютере, на котором размещается экземпляр SQL Server R Services.

## <a name="post-installation-tasks"></a>Действия после установки

Чтобы настроить другой экземпляр Microsoft R Server с теми же параметрами, можно повторно использовать файл конфигурации, созданный во время установки. Дополнительные сведения см. в разделе [Установка SQL Server с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).

### <a name="review-installed-components"></a>Проверка установки компонентов

После завершения установки можно просмотреть файл конфигурации, созданный программой установки SQL Server, а также сводку по действиям установки.

По умолчанию все сводные данные и журналы установки для SQL Server и связанные функции создаются в следующих папках:

+ SQL Server 2017: `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`
+ SQL Server 2016:  `C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`

Для каждого компонента, установленного создается отдельный вложенная папка.

### <a name="customize-the-r-or-python-environment"></a>Настройка среды R или Python

После установки можно установить дополнительные пакеты R или Python. Процесс отличается в зависимости от того, используется ли SQL Server 2016 или 2017 г. SQL Server.

В SQl Server 2017 г можно установить и управлять пакеты R с помощью T-SQL. Дополнительные сведения см. в разделе [Установка и управление пакеты R](../r/install-additional-r-packages-on-sql-server.md).

Python, а в SQL Server 2016 администратор должен установить все дополнительные библиотеки, которые могут быть необходимы.

> [!IMPORTANT]
> Если вы собираетесь выполнять код R на сервере SQL Server, убедитесь, что установки те же пакеты на компьютере, который будет использоваться для разработки решения и экземпляр SQL Server для последующего выполнения либо развернуть решение.

### <a name="upgrading-r-server-or-sql-server-machine-learning"></a>Обновление R Server или SQL Server машинного обучения

Если вы не собираетесь использовать SQL Server, можно установить Microsoft R Server или машины обучения с помощью отдельного установщика Windows. Для места загрузки и инструкции найти по следующим ссылкам:

+ [Установка машинного обучения для Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установка R Server 9.0.1 для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) 

Установщик отдельных окон для машины обучения Server может также использоваться для обновления машинного обучения компонентов, связанных с экземпляром.  Для просмотра дополнительных сведений перейдите по следующим ссылкам:

+ [Использовать SqlBindR обновления R](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
