---
title: Установка пакетов с инструментами R
description: Сведения об использовании стандартных инструментов R для установки новых пакетов R в экземпляре Служб машинного обучения SQL Server или служб SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/20/2019
ms.topic: how-to
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: dd9b0dde6a7cc032b31fc2d8c45a06f616e3ed58
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179186"
---
# <a name="install-packages-with-r-tools"></a>Установка пакетов с инструментами R

[!INCLUDE [SQL Server 2016 and 2017 only](../../includes/applies-to-version/sqlserver2016-2017-only.md)]

В этой статье описывается использование стандартных инструментов R для установки новых пакетов R в экземпляре Служб машинного обучения SQL Server или служб SQL Server R Services. Пакеты можно устанавливать на SQL Server как с подключенным Интернетом, так и без него.

Помимо стандартных средств R, пакеты R можно также установить с помощью:

+ [RevoScaleR](install-r-packages-with-revoscaler.md)
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
+ [T-SQL](install-r-packages-with-tsql.md) (CREATE ANY EXTERNAL LIBRARY).
::: moniker-end

## <a name="general-considerations"></a>Общие рекомендации

+ Код R, выполняющийся в SQL Server, может использовать только пакеты, установленные в библиотеке экземпляра по умолчанию. SQL Server не может загружать пакеты из внешних библиотек, даже если эти библиотеки находятся на том же компьютере.
В их число входят библиотеки R, установленные с другими продуктами Майкрософт.

+ Библиотека пакетов R находится в папке Program Files своего экземпляра SQL Server и по умолчанию для установки в этой папке требуются права администратора. Дополнительные сведения см. в статье [Расположение библиотеки пакетов](../package-management/r-package-information.md#default-r-library-location).

  ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
  Пользователи без прав администратора могут устанавливать пакеты с помощью RevoScaleR 9.0.1 и более поздней версии или с помощью инструкции CREATE EXTERNAL LIBRARY. Пользователь **dbo_owner** или пользователь с разрешением на инструкцию CREATE EXTERNAL LIBRARY может устанавливать пакеты R в текущую базу данных. Дополнительные сведения см. в разделе:
  + [Установка пакетов R с помощью RevoScaleR](install-r-packages-with-revoscaler.md)
  + [Использование инструкции T-SQL (CREATE EXTERNAL LIBRARY) для установки пакетов R на SQL Server](install-r-packages-with-tsql.md)
  ::: moniker-end

  ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  Пользователи без прав администратора могут устанавливать пакеты с помощью RevoScaleR 9.0.1 и более поздней версии. Пользователь **dbo_owner** может устанавливать пакеты R в текущую базу данных. Дополнительные сведения см. в статье [Установка пакетов R с помощью RevoScaleR](install-r-packages-with-revoscaler.md).
  ::: moniker-end

+ В защищенной среде SQL Server может потребоваться отказаться от следующих пакетов:
  + пакеты, которым требуется доступ к сети;
  + пакеты, которым требуется доступ к файловой системе с повышенными правами;
  + пакеты, используемые для веб-разработки или других задач, малоэффективных в SQL Server.

## <a name="online-installation-with-internet-access"></a>Оперативная установка (с доступом к Интернету)

Если SQL Server имеет доступ к Интернету, то для установки пакетов R можно использовать стандартные инструменты.

1. Определите расположение библиотеки экземпляра (см. статью о [получении сведений о пакете R](../package-management/r-package-information.md)) и перейдите к папке, куда установлены инструменты R.

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   Например, путь по умолчанию для стандартного экземпляра SQL Server такой:

   `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64\`
   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   Например, путь по умолчанию для стандартного экземпляра SQL Server такой:

   `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`
   ::: moniker-end

1. В этой папке от имени администратора запустите **R** или **RGUI**.

1. Запустите команду R `install.packages` и укажите имя пакета. Если у пакета есть зависимости, установщик автоматически скачает нужные зависимости и установит их.

При наличии нескольких параллельных экземпляров SQL Server запустите установку отдельно для каждого экземпляра, в котором будет использоваться пакет. Пакеты не могут совместно использоваться разными экземплярами.

## <a name="offline-installation-no-internet-access"></a><a name = "bkmk_offlineInstall"></a> Автономная установка (без доступа к Интернету)

Часто на серверах, где размещены рабочие базы данных, нет подключения к Интернету. Для установки пакетов R в этой среде необходимо заранее скачать и подготовить пакеты и зависимости (в виде ZIP-файлов), а затем скопировать файлы в папку на сервере. После размещения этих файлов пакеты можно устанавливать в автономном режиме.

Могут возникнуть сложности с определением всех зависимостей. Для R рекомендуется создать локальный репозиторий с помощью [**miniCRAN**](https://andrie.github.io/miniCRAN/).
**miniCRAN** принимает список пакетов, которые необходимо установить, анализирует зависимости и собирает все необходимые ZIP-файлы. Затем он создает один репозиторий, который можно скопировать в изолированный экземпляр SQL Server. Пакет [**igraph**](https://igraph.org/r/) также полезен при анализе зависимостей пакетов.

Дополнительные сведения см. в статье [Create a local R package repository using miniCRAN](create-a-local-package-repository-using-minicran.md) (Создание локального репозитория пакетов R с помощью miniCRAN).

Когда ZIP-файл будет в экземпляре SQL Server, его можно установить на сервере с помощью стандартных инструментов R.

1. Определите расположение библиотеки экземпляра (см. статью о [получении сведений о пакете R](../package-management/r-package-information.md)) и перейдите к папке, куда установлены инструменты R. 

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   Например, путь по умолчанию для стандартного экземпляра SQL Server такой:

   `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64\`
   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   Например, путь по умолчанию для стандартного экземпляра SQL Server такой:

   `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`
   ::: moniker-end

1. В этой папке от имени администратора запустите **R** или **RGUI**.

1. Выполните команду R `install.packages` и укажите имя пакета или репозитория, а также расположение ZIP-файлов. Пример:

   ```R
   install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
   ```

   Эта команда извлекает пакет R `mynewpackage` из локального ZIP-файла и устанавливает его. Если у пакета есть зависимости, установщик проверяет наличие существующих пакетов в библиотеке. Если вы создали репозиторий, включающий зависимости, установщик также установит необходимые пакеты.

   > [!NOTE]
   > Если необходимые пакеты отсутствуют в библиотеке экземпляров и не найдены в ZIP-файлах, установка целевого пакета завершается сбоем.

В качестве альтернативы использованию **miniCRAN**, можно выполнить следующие действия вручную:

1. Определите все зависимости пакета.
1. Проверьте, установлены ли на сервере необходимые пакеты. Если пакет установлен, проверьте правильность версии.
1. Загрузите пакет и все зависимости на отдельный компьютер с доступом к Интернету.
1. Разместите пакет и зависимости в одном архиве.
1. Создайте ZIP-файл, если его еще нет.
1. Переместите файлы в папку, доступную для сервера.
1. Запустите поддерживаемую команду установки или инструкцию DDL, чтобы установить пакет в библиотеку экземпляров.

## <a name="see-also"></a>См. также раздел

+ [Получение сведений о пакете R](r-package-information.md)
+ [Советы по использованию пакетов R](tips-for-using-r-packages.md)
+ [Учебники по языку R в SQL Server](../tutorials/sql-server-r-tutorials.md)
