---
title: Учебник по Python. Прокат лыж
description: В этом учебнике вы будете использовать Python и линейную регрессию в Службах машинного обучения SQL Server для прогнозирования количества прокатов лыж.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 927816988be8882d4149115f6d4aee38dd3a8f3f
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727033"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Учебник по Python. Прогнозирование проката лыж с помощью линейной регрессии в Службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом учебнике, состоящем из четырех частей, вы будете использовать Python и линейную регрессию в [Службах машинного обучения SQL Server](../what-is-sql-server-machine-learning.md) для прогнозирования количества прокатов лыж. В этом учебнике используется [записная книжка Python в Azure Data Studio](../../azure-data-studio/sql-notebooks.md), но также можно использовать собственную интегрированную среду разработки (IDE) Python.

Представьте, что вы являетесь владельцем компании по прокату лыж и хотите спрогнозировать количество прокатов за некоторый будущий период. Эта информация поможет вам подготовить инвентарь, персонал и пункты проката.

В первой части учебника вы установите необходимые компоненты. Во второй и третьей частях вы напишите скрипты Python в записной книжке Jupyter для подготовки данных и обучения модели машинного обучения. Затем в третьей части вы запустите эти скрипты Python в SQL Server с помощью хранимых процедур T-SQL.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Импорт примера базы данных в SQL Server 

Во [второй части](python-ski-rental-linear-regression-prepare-data.md) вы узнаете, как загружать данные из SQL Server в кадр данных Python, а также подготавливать данные в Python.

В [третьей части](python-ski-rental-linear-regression-train-model.md) вы узнаете, как обучить модель машинного обучения линейной регрессии в Python.

В [четвертой части](python-ski-rental-linear-regression-deploy-model.md) вы узнаете, как сохранить модель в SQL Server, а затем создать хранимые процедуры на основе сценариев Python, разработанных во второй и третьей частях. Хранимые процедуры будут запускаться в SQL Server, чтобы сформировать прогнозы на основе новых данных.

## <a name="prerequisites"></a>предварительные требования

* Службы машинного обучения SQL Server: сведения об установке служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md) или [руководстве по установке для Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Интегрированная среда разработки Python: в этом учебнике используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. в статье [Использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Вы также можете использовать собственную интегрированную среду разработки Python, например записную книжку Jupyter или [Visual Studio Code](https://code.visualstudio.com/docs) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) и [расширением MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* Пакет [revoscalepy](../python/ref-py-revoscalepy.md) — пакет **revoscalepy** входит в состав Служб машинного обучения SQL Server. Чтобы использовать пакет на клиентском компьютере, см. описание вариантов локальной установки этого пакета в разделе [Настройка клиента обработки и анализа данных для разработки на Python](../python/setup-python-client-tools-sql.md).

    Если вы используете записную книжку Python в Azure Data Studio, выполните следующие дополнительные действия, чтобы использовать **revoscalepy**:

    1. Откройте Azure Data Studio.
    1. В меню **Файл** последовательно выберите команды **Настройки** и **Параметры**.
    1. Разверните узел **Расширения** и выберите **Конфигурация записной книжки**
    1. В разделе **Путь Python** введите путь, по которому установлены библиотеки (например, `C:\path-to-python-for-mls`).
    1. Установите флажок **Use Existing Python** (Использовать существующий Python).
    1. Перезапустите Azure Data Studio.

    Если вы используете другую интегрированную среду разработки Python, выполните аналогичные действия для своей среды.

* Инструмент SQL-запросов — в этом учебнике предполагается, что вы используете [Azure Data Studio](../../azure-data-studio/what-is.md). Можно также использовать [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Дополнительные пакеты Python — в примерах этой серии учебников используются пакеты Python, которые могут быть как установлены, так и не установлены вами. При необходимости для установки пакетов используйте команды **pip**.

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Восстановление примера базы данных

Пример набора данных, используемый в этом учебнике, был сохранен в файл резервной копии базы данных **BAK**, чтобы его можно было скачать и использовать.

1. Скачайте файл [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Следуйте инструкциям из раздела [Восстановление базы данных из файла резервной копии](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) в Azure Data Studio, используя следующие сведения:

   * Выполните импорт из скачанного файла **TutorialDB.bak**.
   * Назовите целевую базу данных "TutorialDB".

1. Чтобы убедиться, что набор данных существует после восстановления базы данных, выполните запрос к таблице **dbo.rental_data**:

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Дальнейшие действия

В первой части этого учебника вы выполнили следующие действия:

* Установка необходимых компонентов
* Импорт примера базы данных в SQL Server

Чтобы подготовить данные из базы данных TutorialDB, перейдите ко второй части этого учебника:

> [!div class="nextstepaction"]
> [Учебник по Python. Подготовка данных для обучения модели линейной регрессии](python-ski-rental-linear-regression-prepare-data.md)