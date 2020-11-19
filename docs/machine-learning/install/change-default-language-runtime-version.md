---
title: Изменение стандартной версии языковой среды выполнения R или Python
description: Узнайте, как изменить стандартную версию среды выполнения R или Python, используемую экземпляром SQL в Службах машинного обучения SQL Server 2017 или SQL Server R Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/14/2020
ms.topic: how-to
author: garyericson
ms.author: garye
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 457d728bd0e4abb5c2cf70063c0330924104c482
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869988"
---
# <a name="change-the-default-r-or-python-language-runtime-version"></a>Изменение стандартной версии языковой среды выполнения R или Python

[!INCLUDE[SQL Server 2016 and 2017 only](../../includes/applies-to-version/sqlserver2016-2017-only.md)]

Эта статья содержит сведения об изменении стандартной версии языка R или Python, используемой в [SQL Server 2016 R Services](../r/sql-server-r-services.md) или [Службах машинного обучения SQL Server 2017](../sql-server-machine-learning-services.md).

Ниже перечислены версии языковой среды выполнения R и Python, которые включены в различные версии SQL Server.

| Версия SQL Server | Служба | Накопительное обновление | Версии среды выполнения R | Версия среды выполнения Python |
|-|-|-|-|-|
| SQL Server 2016 | Службы R | RTM — с пакетом обновления 2 (SP2) CU13 | 3.2.2 | Недоступно |
| SQL Server 2016 | Службы R | Пакет обновления 2 (SP2 ) CU14 и более поздние версии | 3.2.2 и 3.5.2 | Недоступно |
| SQL Server 2017 | Служба машинного обучения | RTM — CU21 | 3.3.3 | 3.5.2 |
| SQL Server 2017 | Служба машинного обучения | CU22 и более поздние версии | 3.3.3 и 3.5.2 | 3.5.2 и 3.7.2 |

## <a name="prerequisites"></a>Предварительные условия

Необходимо установить накопительное обновление (CU), чтобы изменить стандартную версию языковой среды выполнения R или Python:

- **SQL Server 2016:** пакет обновления (SP) 2, накопительное обновление (CU) 14 или более поздней версии.
- **SQL Server 2017:** накопительное обновление (CU) 22 или более поздней версии.

Чтобы скачать последний накопительный пакет обновлений, перейдите на страницу [Последние обновления для Microsoft SQL Server](../../database-engine/install-windows/latest-updates-for-microsoft-sql-server.md).

> [!NOTE]
> При интегрировании накопительного обновления с новой установкой SQL Server будут установлены только последние версии среды выполнения R и Python.

## <a name="change-r-runtime-version"></a>Изменение версии среды выполнения R

Если вы установили одно из приведенных выше накопительных обновлений для SQL Server 2016 или 2017, в экземпляре SQL может быть несколько версий R. Каждая версия содержится во вложенной папке экземпляра с именем `R_SERVICES.`*&lt;major&gt;* . *&lt;minor&gt;* (папка из исходной установки может не иметь номера версии, добавленного к имени папки).

При установке пакета CU, содержащего R 3.5, создается папка `R_SERVICES`:

- SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.<INSTANCE_NAME>\R_SERVICES.3.5`.
- SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<INSTANCE_NAME>\R_SERVICES.3.5`.

Каждый экземпляр SQL использует одну из этих версий в качестве стандартной версии R. Стандартную версию можно изменить с помощью служебной программы командной строки **RegisterRext.exe**. Эта программа находится в папке R в каждом экземпляре SQL:

*&lt;путь_к_экземпляру_SQL&gt;* \R_SERVICES.n.n\library\RevoScaleR\rxLibs\x64\RegisterRext.exe

> [!Note]
> Возможности, описываемые в этой статье, доступны только с копией **RegisterRext.exe**, включенной в пакеты CU для SQL. Не используйте копию, поставляемую с исходной установкой SQL.

Чтобы изменить версию среды выполнения R, передайте следующие аргументы командной строки в **RegisterRext.exe**:

- `/configure` — обязательный аргумент, который указывает, что вы настраиваете стандартную версию R.

- `/instance:`*&lt;имя_экземпляра&gt;*  — необязательно, экземпляр, который нужно настроить. Если он не указан, настраивает экземпляр, заданный по умолчанию.

- `/rhome:`*&lt;путь_к_папке_R_SERVICES[n.n]&gt;*  — необязательно, путь к папке версии среды выполнения, которую вы хотите задать в качестве стандартной версии R.

  Если не указать /rhome, будет указан путь, по которому располагается **RegisterRext.exe**.

### <a name="examples"></a>Примеры

Ниже приведены примеры изменения версии среды выполнения R в SQL Server 2016 и 2017.

#### <a name="change-r-runtime-version-in-sql-server-2016"></a>Изменение версии среды выполнения R в SQL Server 2016

Например, чтобы настроить **R 3.5** в качестве стандартной версии R для экземпляра MSSQLSERVER01 в SQL Server 2016, сделайте следующее:

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES.3.5\library\RevoScaleR\rxLibs\x64"

.\RegisterRext.exe /configure /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES.3.5" /instance:MSSQLSERVER01
```

#### <a name="change-r-runtime-version-in-sql-server-2017"></a>Изменение версии среды выполнения R в SQL Server 2017

Например, чтобы настроить **R 3.5** в качестве стандартной версии R для экземпляра MSSQLSERVER01 в SQL Server 2017, сделайте следующее:

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\R_SERVICES.3.5\library\RevoScaleR\rxLibs\x64"

.\RegisterRext.exe /configure /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\R_SERVICES.3.5" /instance:MSSQLSERVER01
```

В этих примерах не нужно включать аргумент `/rhome`, так как вы указываете ту же папку, в которой расположена служебная программа **RegisterRext.exe**.

## <a name="change-python-runtime-version"></a>Изменение версии среды выполнения Python

Если вы установили CU22 или более поздней версии для SQL Server 2017, в экземпляре SQL может быть несколько версий Python. Каждая версия содержится во вложенной папке экземпляра с именем `PYTHON_SERVICES.`*&lt;major&gt;* . *&lt;minor&gt;* (папка из исходной установки может не иметь номера версии, добавленного к имени папки).

Например, при установке пакета CU, содержащего Python 3.7, создается папка `PYTHON_SERVICES`:

`C:\Program Files\Microsoft SQL Server\MSSQL14.<INSTANCE_NAME>\PYTHON_SERVICES.3.7`  

Каждый экземпляр SQL использует одну из этих версий в качестве стандартной версии Python. Стандартную версию можно изменить с помощью служебной программы командной строки **RegisterRExt.exe**. Эта программа находится в папках Python в каждом экземпляре SQL:

*&lt;путь_к_экземпляру_SQL&gt;* `\PYTHON_SERVICES.n.n\Lib\site-packages\revoscalepy\rxLibs\RegisterRExt.exe`

> [!Note]
> Возможности, описываемые в этой статье, доступны только с копией **RegisterRExt.exe**, включенной в пакеты CU для SQL. Не используйте копию, поставляемую с исходной установкой SQL.

Чтобы изменить версию среды выполнения Python, передайте следующие аргументы командной строки в **RegisterRext.exe**:

- `/configure` — обязательный аргумент, который указывает, что вы настраиваете стандартную версию Python.

- `/python` — указывает, что вы настраиваете стандартную версию Python. Необязательно, если указано `/pythonhome`.

- `/instance:`*&lt;имя_экземпляра&gt;*  — необязательно, экземпляр, который нужно настроить. Если он не указан, настраивает экземпляр, заданный по умолчанию.

- `/pythonhome:`*&lt;путь_к_папке_PYTHON_SERVICES[n.n]&gt;*  — необязательно, путь к папке версии среды выполнения, которую вы хотите задать в качестве стандартной версии Python.

  Если не указать /pythonhome, будет указан путь, по которому располагается **RegisterRExt.exe**.

### <a name="example"></a>Пример

Например, чтобы настроить **Python 3.7** в качестве версии Python по умолчанию для экземпляра MSSQLSERVER01 в SQL Server 2017, сделайте следующее:

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\PYTHON_SERVICES.3.7\Lib\site-packages\revoscalepy\rxLibs"

.\RegisterRext.exe /configure /pythonhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES.3.7" /instance:MSSQLSERVER01
```

В этом примере не нужно включать аргумент `/pythonhome`, так как вы указываете ту же папку, в которой расположена служебная программа **RegisterRext.exe**.

## <a name="remove-a-runtime-version"></a>Удаление версии среды выполнения

Чтобы удалить версию R или Python, используйте **RegisterRExt.exe** с аргументом командной строки `/cleanup`. Используйте те же аргументы `/rhome`, `/pythonhome` и `/instance`, которые описаны выше.

Например, чтобы удалить папку **R 3.2** из экземпляра MSSQLSERVER01, сделайте следующее:

```cmd
.\RegisterRext.exe /cleanup /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES" /instance:MSSQLSERVER01
```

Например, чтобы удалить папку **Python 3.7** из экземпляра MSSQLSERVER01, сделайте следующее:

```cmd
.\RegisterRExt.exe /cleanup /python /pythonhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\PYTHON_SERVICES.3.7" /instance:MSSQLSERVER01
```

**RegisterRext.exe** предложит подтвердить очистку указанной среды выполнения R:

> *Вы действительно хотите окончательно удалить указанную среду выполнения вместе со всеми установленными в ней пакетами? \[Да(Y)/Нет(N)/По умолчанию(Да)\]:*

Для подтверждения введите `Y` или нажмите клавишу ВВОД. Кроме того, можно пропустить этот запрос, передав `/y` или `/Yes` в параметр `/cleanup`.

> [!NOTE]
> Версию можно удалить только в том случае, если она не настроена в качестве стандартной версии и в настоящее время не используется для запуска **RegisterRext.exe**.

## <a name="next-steps"></a>Дальнейшие шаги

- [Получение сведений о пакете R](../package-management/r-package-information.md)
- [Получение сведений о пакете Python](../package-management/python-package-information.md)
- [Установка пакетов с инструментами R](../package-management/install-r-packages-standard-tools.md)
- [Установка пакетов с инструментами Python](../package-management/install-python-packages-standard-tools.md)
