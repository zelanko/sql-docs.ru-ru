---
title: Подключения к главному узлу и HDFS
titleSuffix: SQL Server 2019 big data clusters
description: Узнайте, как подключаться к основной экземпляр SQL Server и шлюза HDFS или Spark для кластера SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9129b436f33092054a19b858fa5bcdb8aebadec2
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241825"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio

В этой статье описывается подключение к кластеру больших данных SQL Server 2019 (Предварительная версия) из среды Studio данных Azure.

## <a name="prerequisites"></a>предварительные требования

- Развернутый [кластера больших данных SQL Server 2019](deployment-guidance.md).
- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

## <a name="connect-to-the-cluster"></a>Подключитесь к кластеру

При подключении к кластеру больших данных, у вас есть возможность подключения к основной экземпляр SQL Server или к шлюзу HDFS или Spark. Ниже показано, как подключиться к каждому.

## <a id="master"></a> Основной экземпляр

Основной экземпляр SQL Server — это традиционные экземпляр SQL Server, содержащий реляционных баз данных SQL Server. Следующие шаги описывают, как подключиться к основной экземпляр с помощью студии данных Azure.

1. Из командной строки найти IP-адрес главного экземпляра с помощью следующей команды:

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. В Azure данных Studio нажмите клавишу **F1** > **новое подключение**.

1. В **тип подключения**выберите **Microsoft SQL Server**.

1. Введите IP-адрес главного экземпляра SQL Server в **имя_сервера** (например: **\<IP-адрес\>, 31433**).

1. Введите имя входа SQL **имя пользователя** и **пароль**.

   > [!TIP]
   > По умолчанию является имя пользователя **SA** и, если не изменено, пароль соответствует **MSSQL_SA_PASSWORD** переменной среды, используемый во время развертывания.

1. Изменить целевой объект **имя базы данных** к одному из реляционных баз данных.

   ![Подключиться к основной экземпляр](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Нажмите клавишу **Connect**и **панель мониторинга сервера** должен отображаться.

## <a id="hdfs"></a> Шлюз HDFS и Spark

**HDFS/Spark шлюза** позволяет подключать для работы с пулом носителей HDFS и для выполнения заданий Spark. Следующие шаги описывают способ подключения с помощью Azure Data Studio.

1. Из командной строки найти IP-адрес шлюза HDFS/Spark с помощью одного из следующих команд.
   
   **AKS развертываний:**

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```

   **Развертывание AKS не**:

   ```
   kubectl get svc service-security-nodeport -n <your-cluster-name>
   ```
 
1. В Azure данных Studio нажмите клавишу **F1** > **новое подключение**.

1. В **тип подключения**выберите **кластера больших данных в SQL Server**.

   > [!TIP]
   > Если вы не видите **кластера больших данных в SQL Server** подключения введите, убедитесь, что вы установили [расширение SQL Server 2019](../azure-data-studio/sql-server-2019-extension.md) и перезагрузка студии данных после завершения расширения Установка.

1. Введите IP-адрес кластера больших данных в **имя_сервера** (не указать порт).

1. Введите `root` для **пользователя** и укажите **пароль** к кластеру больших данных.

   ![Подключение к шлюзу HDFS и Spark](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > По умолчанию является имя пользователя **корневой** и соответствующий пароль **KNOX_PASSWORD** переменной среды, используемый во время развертывания.

1. Нажмите клавишу **Connect**и **панель мониторинга сервера** должен отображаться.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах SQL Server 2019 большие данные см. в разделе [что такое большие данные кластеры SQL Server 2019](big-data-cluster-overview.md).