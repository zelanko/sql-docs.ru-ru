---
title: Учебник по Python. Прокат лыж
titleSuffix: SQL machine learning
description: В этом цикле учебников, состоящем из четырех частей, вы узнаете, как создать модель линейной регрессии в Python, чтобы прогнозировать число прокатов лыж с помощью машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b34687440763f2c514016989542ae3f2d7c0e6ed
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606920"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-with-sql-machine-learning"></a>Учебник по Python. Прогнозирование проката лыж с помощью линейной регрессии и машинного обучения SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этом цикле учебников, состоящем из четырех частей, вы будете использовать Python и линейную регрессию в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) или [Кластерах больших данных](../../big-data-cluster/machine-learning-services.md) для прогнозирования количества прокатов лыж. В этом учебнике используется [записная книжка Python в Azure Data Studio](../../azure-data-studio/sql-notebooks.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этом учебнике, состоящем из четырех частей, вы будете использовать Python и линейную регрессию в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) для прогнозирования количества прокатов лыж. В этом учебнике используется [записная книжка Python в Azure Data Studio](../../azure-data-studio/sql-notebooks.md).
::: moniker-end

Представьте, что вы являетесь владельцем компании по прокату лыж и хотите спрогнозировать количество прокатов за некоторый будущий период. Эта информация поможет вам подготовить инвентарь, персонал и пункты проката.

В первой части учебника вы установите необходимые компоненты. Во второй и третьей частях вы создадите сценарии Python в записной книжке для подготовки данных и обучения модели машинного обучения. Затем в третьей части вы запустите эти скрипты Python в SQL Server с помощью хранимых процедур T-SQL.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Импорт примера базы данных в SQL Server 

Во [второй части](python-ski-rental-linear-regression-prepare-data.md) вы узнаете, как загрузить данные из базы данных в кадр данных Python, а также подготовить данные в Python.

В [третьей части](python-ski-rental-linear-regression-train-model.md) вы узнаете, как обучить модель машинного обучения линейной регрессии в Python.

В [четвертой части](python-ski-rental-linear-regression-deploy-model.md) вы узнаете, как сохранить модель в базе данных, а затем создать хранимые процедуры на основе сценариев Python, разработанных во второй и третьей частях. Хранимые процедуры будут запускаться на сервере, чтобы формировать прогнозы на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* Службы машинного обучения SQL Server: сведения об установке служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md) или [руководстве по установке для Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Можно также [включить Службы машинного обучения в кластерах больших данных SQL Server](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* Службы машинного обучения SQL Server — сведения об установке служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end

* Интегрированная среда разработки Python: в этом учебнике используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. в статье [Использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

* Инструмент SQL-запросов — в этом учебнике предполагается, что вы используете [Azure Data Studio](../../azure-data-studio/what-is.md).

* Дополнительные пакеты Python. В примерах этой серии учебников используются пакеты Python, которые не могут быть установлены по умолчанию.

  * pandas
  * pyodbc
  * sklearn

  Чтобы установить эти пакеты, выполните приведенные ниже действия.
  1. В Azure Data Studio выберите **Управление пакетами**.
  2. В области **Управление пакетами** выберите вкладку **Добавить новые**.
  3. Для каждого из следующих пакетов введите имя пакета, щелкните **Поиск**, а затем **Установить**.

  В качестве альтернативы можно открыть **командную строку**, изменить путь установки для версии Python, используемой в Azure Data Studio (например, `cd %LocalAppData%\Programs\Python\Python37-32`), а затем выполнить `pip install` для каждого пакета.

## <a name="restore-the-sample-database"></a>Восстановление примера базы данных

Пример базы данных, используемый в этом учебнике, сохранен в файл резервной копии базы данных **BAK**, чтобы его можно было скачать и использовать.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Если вы используете Службы машинного обучения в Кластерах больших данных, ознакомьтесь со статьей [Восстановление базы данных на главном экземпляре кластера больших данных SQL Server](../../big-data-cluster/data-ingestion-restore-database.md).
::: moniker-end

1. Скачайте файл [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Следуйте инструкциям из раздела [Восстановление базы данных из файла резервной копии](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) в Azure Data Studio, используя следующие сведения:

   * Выполните импорт из скачанного файла **TutorialDB.bak**.
   * Назовите целевую базу данных "TutorialDB".

1. Чтобы убедиться, что восстановленная база данных существует, выполните запрос к таблице **dbo.rental_data**:

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

1. Включите внешние скрипты, выполнив следующие команды SQL:

    ```sql
    sp_configure 'external scripts enabled', 1;
    RECONFIGURE WITH override;
    ```

## <a name="next-steps"></a>Дальнейшие действия

В первой части этого учебника вы выполнили следующие действия:

* Установка необходимых компонентов
* Импорт примера базы данных в SQL Server

Чтобы подготовить данные из базы данных TutorialDB, перейдите ко второй части этого учебника:

> [!div class="nextstepaction"]
> [Учебник по Python. Подготовка данных для обучения модели линейной регрессии](python-ski-rental-linear-regression-prepare-data.md)