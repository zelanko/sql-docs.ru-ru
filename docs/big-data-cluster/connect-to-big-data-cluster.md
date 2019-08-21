---
title: Подключение к кластерам больших данных в главном и HDFS
description: Узнайте, как подключиться к экземпляру SQL Server master и шлюзу HDFS/Spark для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fb6e1f684a277740c06fbd0a2fdc23dbd77f8e5c
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652421"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается подключение к [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] из Azure Data Studio.

## <a name="prerequisites"></a>Предварительные требования

- Развернутый [кластер больших данных SQL Server 2019](deployment-guidance.md).
- [Средства для работы с большими данными SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

## <a id="master"></a> Подключение к кластеру

Чтобы подключиться к кластеру больших данных с помощью Azure Data Studio, установите новое подключение к главному экземпляру SQL Server в кластере. Далее описывается процедура подключения к главному экземпляру с помощью Azure Data Studio.

1. В командной строке определите IP-адрес главного экземпляра с помощью следующей команды:

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Если вы не изменили соответствующие настройки в файле конфигурации развертывания, кластеру больших данных по умолчанию присваивается имя **mssql-cluster**. Дополнительные сведения см. в статье [Настройка параметров развертывания для кластеров больших данных](deployment-custom-configuration.md#clustername).

1. В Azure Data Studio нажмите **F1** > **Создать подключение**.

1. В разделе **Тип подключения** выберите **Microsoft SQL Server**.

1. Введите IP-адрес главного экземпляра SQL Server в поле **Имя сервера** (например, **\<IP-адрес\>,31433**).

1. Введите **имя пользователя** и **пароль** для входа в SQL.

   > [!TIP]
   > По умолчанию применяется имя пользователя **SA**. Если конфигурация не изменялась, пароль соответствует значению переменной среды **MSSQL_SA_PASSWORD**, используемой во время развертывания.

1. В поле **Имя базы данных** укажите в качестве целевой одну из ваших реляционных баз данных.

   ![Подключение к главному экземпляру](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Нажмите **Подключить**. Откроется **панель мониторинга сервера**.

В выпуске Azure Data Studio, который вышел в феврале 2019 года, после установления подключения к главному экземпляру SQL Server вы также сможете работать с шлюзом HDFS/Spark. Это значит, что вам не потребуется отдельное подключение для HDFS и Spark, которое описывается в следующем разделе.

- В обозревателе объектов появится новый узел **Службы данных**. В вызываемом с помощью правой кнопки мыши меню этого узла будут представлены задачи для работы с кластером больших данных, например для создания новых записных книжек или отправки заданий Spark. 
- Узел **Службы данных** также содержит папку **HDFS** для работы с HDFS и выполнения таких действий, как создание внешней таблицы или анализ в записной книжке.
- Если установлено расширение, **панель мониторинга сервера** для подключения также содержит вкладки **Кластер больших данных SQL Server** и **SQL Server 2019 (предварительная версия)** .

   ![Узел служб данных Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]см. в разделе [что [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]такое ](big-data-cluster-overview.md).