---
title: Учебник. Выполнение кластеризации в Python
description: В этой серии руководств из четырех частей вы будете выполнять кластеризацию клиентов в базе данных SQL с помощью Python с SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: abcd13b5db24f7ffd44a21b4690f14d97645cdd5
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211928"
---
# <a name="tutorial-perform-clustering-in-python-with-sql-server-machine-learning-services"></a>Учебник. Выполнение кластеризации в Python с помощью SQL Server Службы машинного обучения

В этой серии руководств из четырех частей вы будете использовать Python для разработки и развертывания модели кластеризации на K-средних в [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md) для данных клиентов кластера.

В первой части этой серии вы настроите предварительные требования для учебника, а затем импортируете образец набора данных в базу данных SQL. Далее в этой серии вы будете использовать эти данные для обучения и развертывания модели кластеризации в Python с помощью SQL Server Службы машинного обучения.

В части 2 и 3 из этой серии вы разрабатываете некоторые сценарии Python в записной книжке Azure Data Studio для анализа и подготовки данных и обучения модели машинного обучения. Затем, в части 4, вы запустите эти скрипты Python в базе данных SQL с помощью хранимых процедур.

*Кластеризацию* можно объяснить как организацию данных в группы, в которых члены группы похожи каким-либо образом. В рамках этой серии руководств вы можете представить себе розничную деятельность. Вы будете использовать алгоритм **K-средних** для выполнения кластеризации клиентов в наборе данных покупок продуктов и возврата. Благодаря кластеризации клиентов вы можете более эффективно сосредоточиться на маркетинговых действиях, нацеливание на конкретные группы.
Кластеризация по-средних — это неконтролируемый алгоритм *обучения* , который ищет закономерности в данных на основе сходства.

Из этой статьи вы узнаете о следующем:

> [!div class="checklist"]
> * Импорт образца базы данных в экземпляр SQL Server

В [части 2](tutorial-python-clustering-model-prepare-data.md)вы узнаете, как подготавливать данные из базы данных SQL для выполнения кластеризации.

В [третьей части](tutorial-python-clustering-model-build.md)вы узнаете, как создать и обучить модель кластеризации K-средних в Python.

В [части 4](tutorial-python-clustering-model-deploy.md)вы узнаете, как создать хранимую процедуру в базе данных SQL, которая может выполнять кластеризацию в Python на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

* [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md) с помощью параметра язык Python. Следуйте инструкциям по установке в руководствах по установке [Windows](../install/sql-machine-learning-services-windows-install.md) или в разделе [руководства по установке Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* Интегрированная среда разработки Python. в этом руководстве используется записная книжка Python в [Azure Data Studio](../../azure-data-studio/what-is.md). Дополнительные сведения см. [в статье использование записных книжек в Azure Data Studio](../../azure-data-studio/sql-notebooks.md). Вы также можете использовать собственную интегрированную среду разработки Python, например записную книжку Jupyter или [Visual Studio Code](https://code.visualstudio.com/docs) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) и [расширением MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).

* пакет [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) — пакет **revoscalepy** входит в SQL Server службы машинного обучения. Сведения о том, как использовать пакет на клиентском компьютере, см. в разделе [Настройка клиента обработки и анализа данных для разработки на Python](../python/setup-python-client-tools-sql.md) с параметрами для установки этого пакета локально.

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
  pip install matplotlib
  pip install scipy
  pip install sklearn
  ```

## <a name="import-the-sample-database"></a>Импорт образца базы данных

Образец набора данных, используемый в этом руководстве, был сохранен в файл резервной копии **. bak** для загрузки и использования. Этот набор данных является производным от [тпккс — BB](http://www.tpc.org/tpcx-bb/default.asp) набора данных, предоставляемого Советом по [производительности обработки транзакций (TPC)](http://www.tpc.org/default.asp).

1. Скачайте файл [tpcxbb_1gb. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) в папку резервного копирования SQL Server. Для экземпляра базы данных по умолчанию используется папка:

   `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\`

1. Откройте Azure Data Studio, подключитесь к экземпляру SQL Server и откройте новое окно запроса.

1. Выполните следующие команды, чтобы восстановить базу данных.

   ```sql
   USE master;
   GO

   RESTORE DATABASE tpcxbb_1gb
   FROM DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\tpcxbb_1gb.bak'
   WITH MOVE 'tpcxbb_1gb' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.mdf'
      , MOVE 'tpcxbb_1gb_log' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.ldf';
   GO
   ```

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим руководством, удалите базу данных tpcxbb_1gb из SQL Server.

## <a name="next-steps"></a>Следующие шаги

В первой части этой серии руководств вы выполнили следующие действия:

* Импорт образца базы данных в экземпляр SQL Server

Чтобы подготовить данные для модели машинного обучения, следуйте второй части этой серии руководств:

> [!div class="nextstepaction"]
> [Учебник. Подготовка данных к кластеризации в Python с помощью SQL Server Службы машинного обучения](tutorial-python-clustering-model-prepare-data.md)
