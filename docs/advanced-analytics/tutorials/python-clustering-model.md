---
title: Учебник по Python. Классификация пользователей
description: В этом учебнике из четырех частей вы выполните кластеризацию клиентов с помощью метода k-средних в базе данных SQL, используя Python вместе со службами машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 245a1566bfbbf19821323d0b474669eaba1d2e6e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727082"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>Руководство. Классификация клиентов на основе кластеризации методом k-средних с помощью служб машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом учебнике из четырех частей вы будете использовать Python для разработки и развертывания модели кластеризации методом k-средних в [Службах машинного обучения SQL Server](../what-is-sql-server-machine-learning.md) для кластеризации данных клиентов.

В первой части этого учебника серии вы настроите необходимые компоненты, а затем восстановите пример набора данных в базе данных SQL. Далее в этой серии руководств вы будете использовать эти данные для обучения и развертывания модели кластеризации с использованием Python в службах машинного обучения SQL Server.

Во второй и третьей частях вы напишите скрипты Python в записной книжке Azure Data Studio для анализа и подготовки данных и обучения модели машинного обучения. Затем в четвертой части вы запустите эти скрипты Python в базе данных SQL с помощью хранимых процедур.

*Кластеризацию* можно описать как организацию данных по группам, где члены группы каким-либо образом похожи друг на друга. В рамках этой серии руководств вы можете представить себя владельцем розничного предприятия. Вы будете использовать метод **k-средних** для кластеризации клиентов в наборе данных о покупках и возвратах продуктов. Благодаря кластеризации клиентов вы можете более эффективно осуществлять маркетинговую деятельность, ориентируясь на конкретные группы.
Кластеризация методом k-средних — это алгоритм *неконтролируемого обучения*, который ищет закономерности в данных на основе сходства.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Восстановление примера базы данных в экземпляре SQL Server

Во [второй части](python-clustering-model-prepare-data.md) вы узнаете, как подготовить данные из базы данных SQL для выполнения кластеризации.

В [третьей части](python-clustering-model-build.md) вы узнаете, как создать и обучить модель кластеризации на основе k-средних в Python.

В [четвертой части](python-clustering-model-deploy.md) вы узнаете, как создать хранимую процедуру в базе данных SQL, которая может выполнять кластеризацию в Python на основе новых данных.

## <a name="prerequisites"></a>предварительные требования

* [Службы машинного обучения SQL Server с языком Python](../what-is-sql-server-machine-learning.md) — следуйте инструкциям по установке в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md) или [руководстве по установке для Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* Интегрированная среда разработки Python: в этом учебнике используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. в статье [Использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md). Вы также можете использовать собственную интегрированную среду разработки Python, например записную книжку Jupyter или [Visual Studio Code](https://code.visualstudio.com/docs) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) и [расширением MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).

* Пакет [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) — пакет **revoscalepy** входит в состав Служб машинного обучения SQL Server. Чтобы использовать пакет на клиентском компьютере, см. описание вариантов локальной установки этого пакета в разделе [Настройка клиента обработки и анализа данных для разработки на Python](../python/setup-python-client-tools-sql.md).

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
  pip install matplotlib
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>Восстановление примера базы данных

Пример набора данных, используемый в этом учебнике, был сохранен в файл резервной копии базы данных **BAK**, чтобы его можно было скачать и использовать. Этот набор данных является производным от набора данных [tpcx-bb](http://www.tpc.org/tpcx-bb/default.asp), предоставляемого [Советом по оценке производительности обработки транзакций (TPC)](http://www.tpc.org/default.asp).

1. Скачайте файл [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak).

1. Следуйте инструкциям из раздела [Восстановление базы данных из файла резервной копии](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) в Azure Data Studio, используя следующие сведения:

   * Выполните импорт из скачанного файла **tpcxbb_1gb.bak**.
   * Назовите целевую базу данных "tpcxbb_1gb".

1. Чтобы убедиться, что набор данных существует после восстановления базы данных, выполните запрос к таблице **dbo.customer**:

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим учебником, удалите базу данных tpcxbb_1gb из SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

В первой части этого учебника вы выполнили следующие действия:

* Восстановление примера базы данных в экземпляре SQL Server

Чтобы подготовить данные из для модели машинного обучения, перейдите ко второй части этого учебника:

> [!div class="nextstepaction"]
> [Учебник. Подготовка данных для кластеризации в Python с помощью Служб машинного обучения SQL Server](python-clustering-model-prepare-data.md)
