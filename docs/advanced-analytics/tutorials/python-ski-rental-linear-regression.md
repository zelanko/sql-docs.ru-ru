---
title: Учебник по Python. Прокат лыж
description: В части три этого четырехсерийного учебника вы создадите линейную модель регрессии на Python для прогнозирования проката лыж в Службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/02/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe8a0c9af06d39ce183677adb86f30d9fc197d67
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75681755"
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

## <a name="prerequisites"></a>Предварительные требования

* Службы машинного обучения SQL Server: сведения об установке служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md) или [руководстве по установке для Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Интегрированная среда разработки Python: в этом учебнике используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. в статье [Использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Вы также можете использовать собственную интегрированную среду разработки Python, например записную книжку Jupyter или [Visual Studio Code](https://code.visualstudio.com/docs) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) и [расширением MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* Инструмент SQL-запросов — в этом учебнике предполагается, что вы используете [Azure Data Studio](../../azure-data-studio/what-is.md). Можно также использовать [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

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

1. Скачайте файл [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Следуйте инструкциям из раздела [Восстановление базы данных из файла резервной копии](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) в Azure Data Studio, используя следующие сведения:

   * Выполните импорт из скачанного файла **TutorialDB.bak**.
   * Назовите целевую базу данных "TutorialDB".

1. Чтобы убедиться, что восстановленная база данных существует, выполните запрос к таблице **dbo.rental_data**:

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

Включите внешние скрипты, выполнив следующие команды SQL:

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