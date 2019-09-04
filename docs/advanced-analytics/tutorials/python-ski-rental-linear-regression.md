---
title: 'Учебник по Python: Ski напрокат (линейная регрессия)'
description: В этом учебнике вы будете использовать Python и линейную регрессию в SQL Server Службы машинного обучения для прогнозирования количества Ski напрокат.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 718487ba55b2b8db8f16b59df5785cf78ff501f1
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242512"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Учебник по Python: Прогнозирование Ski аренд с линейной регрессией в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой серии руководств из четырех частей вы будете использовать Python и линейную регрессию в [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md) для прогнозирования количества Ski напрокат. В этом руководстве используется [Записная книжка Python в Azure Data Studio](../../azure-data-studio/sql-notebooks.md), но можно также использовать собственную интегрированную среду разработки (IDE) Python.

Представьте себе, что вы являетесь владельцем компании Ski аренды и хотите спрогнозировать количество напрокат, которые будут использоваться в будущем. Эта информация поможет вам получить готовые акции, персонал и средства.

В первой части этой серии вы сможете настроить необходимые компоненты. В частях 2 и 3 вы разрабатываете некоторые сценарии Python в записной книжке Jupyter для подготовки данных и обучения модели машинного обучения. Затем, в третьей части, вы запустите эти скрипты Python в SQL Server с помощью хранимых процедур T-SQL.

Из этой статьи вы узнаете о следующем:

> [!div class="checklist"]
> * Импорт образца базы данных в SQL Server 

В [части 2](python-ski-rental-linear-regression-prepare-data.md)вы узнаете, как загружать данные из SQL Server в кадр данных Python, а также подготавливать данные в Python.

В [третьей части](python-ski-rental-linear-regression-train-model.md)вы узнаете, как обучить модель линейной регрессии на Python.

В [части 4](python-ski-rental-linear-regression-deploy-model.md)вы узнаете, как сохранить модель для SQL Server, а затем создать хранимые процедуры из скриптов Python, разработанных в двух и трех частях. Хранимые процедуры будут выполняться в SQL Server, чтобы сделать прогнозы на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

* SQL Server Службы машинного обучения — сведения об установке Службы машинного обучения см. в разделе [руководство по установке Windows](../install/sql-machine-learning-services-windows-install.md) или [руководство по установке Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Интегрированная среда разработки Python. в этом руководстве используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. [в статье использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Вы также можете использовать собственную интегрированную среду разработки Python, например записную книжку Jupyter или [Visual Studio Code](https://code.visualstudio.com/docs) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) и [расширением MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* пакет [revoscalepy](../python/ref-py-revoscalepy.md) — пакет **revoscalepy** входит в SQL Server службы машинного обучения. Сведения о том, как использовать пакет на клиентском компьютере, см. в разделе [Настройка клиента обработки и анализа данных для разработки на Python](../python/setup-python-client-tools-sql.md) с параметрами для установки этого пакета локально.

    Если вы используете записную книжку Python в Azure Data Studio, выполните следующие дополнительные действия, чтобы использовать **revoscalepy**:

    1. Открыть Azure Data Studio
    1. В меню **файл** выберите пункт **настройки** , а затем — **Параметры** .
    1. Разверните узел **расширения** и выберите **Конфигурация записной книжки** .
    1. В разделе **путь Python**введите путь к установленным библиотекам (например, `C:\path-to-python-for-mls`).
    1. Убедитесь, что установлен флажок **использовать существующий Python** .
    1. Перезапустить Azure Data Studio

    Если вы используете другую среду IDE Python, выполните аналогичные действия в интегрированной среде разработки.

* Инструмент SQL-запросов. в этом учебнике предполагается, что вы используете [Azure Data Studio](../../azure-data-studio/what-is.md). Можно также использовать [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Дополнительные пакеты Python. в примерах из этой серии руководств используются пакеты Python, которые вы можете или не установили. Используйте следующие команды **PIP** , чтобы установить эти пакеты при необходимости.

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Восстановление образца базы данных

Образец набора данных, используемый в этом руководстве, был сохранен в файл резервной копии **. bak** для загрузки и использования.

1. Скачайте файл [TutorialDB. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Следуйте инструкциям из раздела [Восстановление базы данных из файла резервной копии](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) в Azure Data Studio, используя следующие сведения:

   * Импорт из скачанного файла **TutorialDB. bak**
   * Назовите целевую базу данных "TutorialDB"

1. Чтобы убедиться, что набор данных существует после восстановления базы данных, выполните запрос к таблице **dbo. rental_data** :

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Следующие шаги

В первой части этой серии руководств вы выполнили следующие действия:

* Предварительные требования установлены
* Импорт образца базы данных в SQL Server

Чтобы подготовить данные из базы данных TutorialDB, следуйте второй части этой серии руководств:

> [!div class="nextstepaction"]
> [Учебник по Python: Подготовка данных для обучения модели линейной регрессии](python-ski-rental-linear-regression-prepare-data.md)