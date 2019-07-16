---
title: Подключения к главному узлу и HDFS
titleSuffix: SQL Server big data clusters
description: Узнайте, как подключаться к основной экземпляр SQL Server и шлюза HDFS или Spark для кластера SQL Server 2019 больших данных (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1f09763b210427c84efe75d693fee302d7048db7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958643"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается подключение к кластеру больших данных SQL Server 2019 (Предварительная версия) из среды Studio данных Azure.

## <a name="prerequisites"></a>предварительные требования

- Развернутый [кластера больших данных SQL Server 2019](deployment-guidance.md).
- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

## <a id="master"></a> Подключитесь к кластеру

Чтобы подключиться к кластерам больших данных с помощью Azure Data Studio, создайте новое подключение к основной экземпляр SQL Server в кластере. Следующие шаги описывают, как подключиться к основной экземпляр с помощью студии данных Azure.

1. Из командной строки найти IP-адрес главного экземпляра с помощью следующей команды:

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > По умолчанию используется имя кластера больших данных **mssql-cluster** Если имя было изменено, в файле конфигурации развертывания. Дополнительные сведения см. в разделе [настроить параметры развертывания для больших данных кластеров](deployment-custom-configuration.md#clustername).

1. В Azure данных Studio нажмите клавишу **F1** > **новое подключение**.

1. В **тип подключения**выберите **Microsoft SQL Server**.

1. Введите IP-адрес главного экземпляра SQL Server в **имя_сервера** (например: **\<IP-адрес\>, 31433**).

1. Введите имя входа SQL **имя пользователя** и **пароль**.

   > [!TIP]
   > По умолчанию является имя пользователя **SA** и, если не изменено, пароль соответствует **MSSQL_SA_PASSWORD** переменной среды, используемый во время развертывания.

1. Изменить целевой объект **имя базы данных** к одному из реляционных баз данных.

   ![Подключиться к основной экземпляр](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Нажмите клавишу **Connect**и **панель мониторинга сервера** должен отображаться.

С выпуском февраля 2019 Studio данных Azure подключении к экземпляру SQL Server master также позволяет взаимодействовать со шлюзом HDFS или Spark. Это означает, что не нужно использовать отдельное соединение для HDFS и Spark, в следующем разделе описывается.

- В обозревателе объектов теперь содержит новый **Data Services** узла с поддержкой щелкните правой кнопкой мыши задачи кластера больших данных, например создание новые записные книжки или отправки заданий spark. 
- **Data Services** узел также содержит **HDFS** папки для просмотра HDFS и выполнения действий, например Create External Table или анализа в записной книжке.
- **Панель мониторинга сервера** для соединения также содержит вкладки для **кластера больших данных в SQL Server** и **2019 SQL Server (Предварительная версия)** при установке расширения.

   ![Узел службы данных Studio данных Azure](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах SQL Server 2019 большие данные см. в разделе [что такое большие данные кластеры SQL Server 2019](big-data-cluster-overview.md).