---
title: Получение сведений о пакете R
description: Узнайте, как получить сведения об установленных пакетах R на SQL Server Службы машинного обучения и SQL Server R Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8c3cf3c1debc03c169c585521b8b46dd8b1365c5
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69641161"
---
# <a name="get-r-package-information"></a>Получение сведений о пакете R

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как получить сведения об установленных пакетах R на SQL Server Службы машинного обучения и SQL Server R Services. Примеры сценариев R показывают, как составить список таких сведений о пакете, как путь и версия установки.

## <a name="default-r-library-location"></a>Расположение библиотеки R по умолчанию

При установке машинного обучения с помощью SQL Server на уровне экземпляра создается отдельная библиотека пакетов для каждого устанавливаемого языка. В Windows библиотека экземпляров является защищенной папкой, зарегистрированной в SQL Server.

Все скрипты, выполняемые в базе данных на SQL Server, должны загружать функции из библиотеки экземпляров. SQL Server не может получить доступ к пакетам, установленным в других библиотеках. Это относится и к удаленным клиентам. любой скрипт R, выполняющийся в контексте вычислений сервера, может использовать только пакеты, установленные в библиотеке экземпляров.
Для защиты серверных ресурсов Библиотека экземпляров по умолчанию может быть изменена только администратором компьютера.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Путь по умолчанию к двоичным файлам для R:

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Путь по умолчанию к двоичным файлам для R:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Путь по умолчанию к двоичным файлам для R:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

Предполагается, что экземпляр SQL по умолчанию — MSSQLSERVER. Если SQL Server устанавливается как определяемый пользователем именованный экземпляр, вместо него используется указанное имя.

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

Выполните следующую инструкцию, чтобы проверить библиотеку пакетов R по умолчанию для текущего экземпляра:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Следующая инструкция использует [рксскллибпасс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) для возврата пути к библиотеке экземпляров и версии RevoScaleR, используемой SQL Server:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Функция [рксскллибпасс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) может выполняться только на локальном компьютере. Функция не может вернуть пути к библиотеке для удаленных соединений.

## <a name="default-r-packages"></a>Пакеты R по умолчанию

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

Следующие пакеты R устанавливаются с SQL Server R Services.

|Пакеты | Version | Описание |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельного выполнения функций Rx для импорта и преобразования данных, моделирования, визуализации и анализа. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | Используется для включения скрипта R в хранимые процедуры. |

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"

Следующие пакеты R устанавливаются с SQL Server Службы машинного обучения при выборе компонента R во время установки.

|Пакеты | Version | Описание |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9,2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельного выполнения функций Rx для импорта и преобразования данных, моделирования, визуализации и анализа. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 9,2 | Используется для включения скрипта R в хранимые процедуры. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 9,2 | Добавляет алгоритмы машинного обучения в R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 9,2 | Используется для написания инструкций многомерных выражений в R. |

::: moniker-end

### <a name="component-upgrades"></a>Обновление компонентов

По умолчанию пакеты R обновляются с помощью пакетов обновления и накопительных обновлений. Дополнительные пакеты и обновление полных версий компонентов R можно выполнять только с помощью обновления продукта или путем привязки поддержки R к Microsoft Machine Learning Server.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Кроме того, вы можете добавлять пакеты MicrosoftML и OLAP в экземпляр SQL Server с помощью обновления компонента.
::: moniker-end

Дополнительные сведения см. [в статье обновление компонентов R и Python в SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-r-packages"></a>Пакеты R с открытым исходным кодом по умолчанию

Поддержка r включает в себя открытый исходный код, позволяющий вызывать базовые функции R и устанавливать дополнительные пакеты с открытым кодом и сторонними производителями. Языковая поддержка R включает в себя базовые функциональные возможности, такие как **базовый**, **Статистика**, **Служебные**программы и другие. В базовую установку R также входят многочисленные образцы наборов данных и стандартные инструменты R, такие как **RGui** (упрощенный интерактивный редактор) и **RTerm** (Командная строка r).

Дистрибутив R с открытым исходным кодом, включенный в установку, — это [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO добавляет значение в базовый R, включая дополнительные пакеты с открытым исходным кодом, например [библиотеку Intel Math Kernel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Версия R, предоставляемая MRO с помощью программы установки SQL Server R Services, — 3.2.2.
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Версия R, предоставляемая MRO с помощью SQL Server Службы машинного обучения установки, — это 3.3.3.
::: moniker-end

> [!IMPORTANT]
> Никогда не следует вручную перезаписывать версию R, установленную SQL Server установки, с более новыми версиями в Интернете. Пакеты Microsoft R основаны на конкретных версиях R. изменение установки может привести к его дестабилизации.

## <a name="list-all-installed-r-packages"></a>Список всех установленных пакетов R

В следующем примере функция `installed.packages()` R используется [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре для вывода списка пакетов R, установленных в библиотеке R_SERVICES для текущего экземпляра SQL. Этот скрипт возвращает поля имени и версии пакета в файле описания.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Дополнительные сведения о необязательном поле и полях по умолчанию для поля Описание пакета R [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)см. в разделе.

## <a name="find-a-single-r-package"></a>Поиск одного пакета R

Если вы установили пакет R и хотите убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить хранимую процедуру для загрузки пакета и возврата сообщений.

Например, следующая инструкция ищет и загружает [связывающий](https://cran.r-project.org/web/packages/glue/) пакет, если он доступен.
Если пакет не удается найти или загрузить, появляется сообщение об ошибке, содержащее текст "не существует пакета с именем" приклеивание ".

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

Дополнительные сведения о пакете см. в `packageDescription`разделе.
Следующая инструкция возвращает сведения для **связывающего** пакета.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>Следующие шаги

+ [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md)
+ [Получение сведений о пакете Python](python-package-information.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Учебники по R и Python](../tutorials/machine-learning-services-tutorials.md)
