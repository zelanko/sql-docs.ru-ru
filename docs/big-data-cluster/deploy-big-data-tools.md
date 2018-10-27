---
title: Подключиться к серверу SQL кластера больших данных с помощью Azure Data Studio | Документация Майкрософт
description: Узнайте, как подключиться к кластеру больших данных SQL Server 2019 с помощью Azure Data Studio.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 18df937cfed15d7302a58267eb392a1933d73052
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643792"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio

В этой статье описывается, как установить Azure Data Studio, расширение SQL Server 2019 (Предварительная версия), и подключитесь к кластеру больших данных. Новое расширение SQL Server 2019 включает в себя поддержку предварительной версии [кластеров SQL Server 2019 больших данных](big-data-cluster-overview.md), интегрированное [записная книжка](notebooks-guidance.md)и PolyBase [мастера Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-azure-data-studio"></a>Установить центр данных Azure

Чтобы установить центр данных Azure, см. в разделе [скачайте и установите последнюю версию Azure Data Studio](../azure-data-studio/download.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Установите расширение SQL Server 2019 (Предварительная версия)

Чтобы установить расширение, см. в разделе [установить расширение SQL Server 2019 (Предварительная версия)](../azure-data-studio/sql-server-2019-extension.md).

## <a name="connect-to-the-cluster"></a>Подключитесь к кластеру

При подключении к кластеру больших данных, у вас есть возможность подключения к SQL Server [главного экземпляра](concept-master-instance.md) или к шлюзу HDFS или Spark. Ниже показано, как подключиться к каждому.

## <a id="master"></a> Основной экземпляр

1. В Azure данных Studio нажмите клавишу **F1** > **новое подключение**.

1. В **тип подключения**выберите **Microsoft SQL Server**.

1. Введите IP-адрес главного экземпляра SQL Server в **имя_сервера** (например:  **\<IP-адрес\>, 31433**).

1. Введите имя входа SQL **имя пользователя** и **пароль**.

1. Изменение **имя базы данных** для **high_value_data** базы данных.

   ![Подключиться к основной экземпляр](./media/deploy-big-data-tools/connect-to-cluster.png)

1. Нажмите клавишу **Connect**и **панель мониторинга сервера** должен отображаться.

## <a id="hdfs"></a> Шлюз HDFS и Spark

1. В Azure данных Studio нажмите клавишу **F1** > **новое подключение**.

1. В **тип подключения**выберите **кластера больших данных в SQL Server**.

1. Введите IP-адрес кластера больших данных в **имя сервера**.

1. Введите `root` для **пользователя** и укажите **пароль** к кластеру больших данных.

   ![Подключение к шлюзу HDFS и Spark](./media/deploy-big-data-tools/connect-to-cluster-hdfs-spark.png)

1. Нажмите клавишу **Connect**и **панель мониторинга сервера** должен отображаться.

## <a name="next-steps"></a>Следующие шаги

Чтобы запустить записных книжек в Azure Data Studio, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).
