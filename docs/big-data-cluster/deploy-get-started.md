---
title: Начало работы
titleSuffix: SQL Server Big Data Clusters
description: Ознакомьтесь с инструкциями и ресурсами по развертыванию Кластеров больших данных SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 396e76852225177b7badcca533faea3ac7cbbe0a
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725905"
---
# <a name="get-started-with-big-data-clusters-2019-deployment"></a>Начало работы по развертыванию [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье содержится обзор развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]. В этой статье рассказывается об основных понятиях и сценариях развертывания. Конкретные шаги по развертыванию зависят от выбора платформ клиента и сервера. Общие сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в разделе [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)

Дополнительные сведения о других сценариях развертывания в SQL Server см. в следующих источниках:

- [Windows](../database-engine/install-windows/install-sql-server.md)
- [Linux](../linux/sql-server-linux-setup.md)
- [Контейнеры Docker](../linux/sql-server-linux-docker-container-deployment.md)

## <a name="quick-introduction"></a>Краткое введение 

Просмотрите это девятиминутное видео, в котором представлены общие сведения о развертывании кластеров больших данных:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Big-Data-Clusters-deployment-overview/player?WT.mc_id=dataexposed-c9-niner]


> [!TIP]
> Чтобы быстро развернуть среду с Kubernetes и кластером больших данных и начать реализовывать ее потенциал, воспользуйтесь одним из примеров сценариев, указанных в [разделе сценариев](#scripts). После развертывания используйте для управления кластером [клиентские средства](#tools), описанные в следующем разделе.


## <a name="client-tools"></a><a id="tools"></a> Клиентские средства

Для кластеров больших данных требуется специальный набор клиентских средств. Перед развертыванием кластера больших данных в Kubernetes необходимо установить обязательные средства. Для разных сценариев требуются разные средства. Каждая статья должна указывать необходимые средства для выполнения определенной задачи. Полный список средств и ссылки для установки см. в разделе [Установка средств для работы с большими данными SQL Server 2019](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

Кластеры больших данных развертываются в виде последовательности взаимосвязанных контейнеров, управляемых в [Kubernetes](https://kubernetes.io/docs/home). Вы можете размещать Kubernetes различными способами. Даже если у вас уже есть среда Kubernetes, ознакомьтесь со связанными требованиями для кластеров больших данных.

- **Служба Azure Kubernetes (AKS)** : AKS позволяет развернуть управляемый кластер Kubernetes в Azure. Управление и обслуживание приходится вести только для узлов агентов. При использовании AKS вам не нужно подготавливать собственное оборудование для кластера. Также можно легко использовать[скрипт Python](quickstart-big-data-cluster-deploy.md) или [записную книжку развертывания](notebooks-deploy.md) для создания кластера AKS и развертывания кластера больших данных за один шаг. Дополнительные сведения о настройке AKS для развертывания кластера больших данных см. в разделе [Настройка службы Azure Kubernetes для развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](deploy-on-aks.md).

- **Azure Red Hat OpenShift (ARO)** . ARO позволяет развертывать управляемый кластер Red Hat OpenShift в Azure. Управление и обслуживание приходится вести только для узлов агентов. При использовании ARO вам не нужно подготавливать собственное оборудование для кластера. Также можно легко использовать [скрипт Python](quickstart-big-data-cluster-deploy-aro.md) для создания кластера ARO и развертывания кластера больших данных за один шаг. Эта модель развертывания появилась в SQL Server 2019 CU5. 

- **Несколько машин**: вы также можете развернуть Kubernetes на нескольких машинах с Linux, которые могут быть физическими серверами или виртуальными машинами. Средство [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) можно использовать для создания кластера Kubernetes. Для автоматизации этого типа развертывания можно использовать [скрипт Bash](deployment-script-single-node-kubeadm.md). Этот метод хорошо работает, если у вас уже есть инфраструктура, которую вы хотите использовать для кластера больших данных. Дополнительные сведения об использовании **kubeadm** для развертывания кластера больших данных см. в разделе [Настройка Kubernetes на нескольких машинах для развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](deploy-with-kubeadm.md).

- **Red Hat OpenShift**. Выполните развертывание в своем собственном кластере Red Hat OpenShift. Дополнительные сведения см. в разделе [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в локальной установке OpenShift и Azure Red Hat OpenShift](deploy-openshift.md). Эта модель развертывания появилась в SQL Server 2019 CU5.

## <a name="deploy-a-big-data-cluster"></a>Развертывание кластера больших данных

После настройки Kubernetes вы развертываете кластер больших данных с помощью команды `azdata bdc create`. При развертывании можно использовать несколько различных подходов.

- При развертывании в среде разработки и тестирования можно использовать [одну из конфигураций](deployment-guidance.md#deploy) по умолчанию, предоставляемых **azdata**.

- Чтобы настроить развертывание, можно создать и использовать собственные [файлы конфигурации развертывания](deployment-guidance.md#configfile).

- Для полностью автоматической установки можно передать все остальные параметры в переменных среды. Дополнительные сведения см. в разделе [Автоматические развертывания](deployment-guidance.md#unattended).


## <a name="deployment-scripts"></a><a id="scripts"></a>Скрипты развертывания

Скрипты развертывания позволяют развертывать как Kubernetes, так и кластеры больших данных за один шаг. Они также часто предоставляют значения по умолчанию для параметров кластера больших данных. Любой скрипт развертывания можно настроить, создав собственную версию, которая настраивает развертывание кластера больших данных особым образом.

Сейчас доступны следующие скрипты развертывания:

- [Развертывание кластера больших данных SQL Server в Службе Azure Kubernetes (AKS) с помощью скрипта Python](quickstart-big-data-cluster-deploy.md)
- [Развертывание кластера больших данных в кластере с одним узлом kubeadm с помощью скрипта Bash](deployment-script-single-node-kubeadm.md)

## <a name="deployment-notebooks"></a>Записные книжки развертывания

Можно также развернуть кластер больших данных, запустив записную книжку Azure Data Studio. Дополнительные сведения о развертывании в AKS с помощью записных книжек см. в следующей статье:

- [Развертывание кластера больших данных с помощью записных книжек Azure Data Studio](notebooks-deploy.md).

## <a name="next-steps"></a>Дальнейшие действия

После успешного развертывания кластера больших данных [подключитесь к кластеру](connect-to-big-data-cluster.md) и рассмотрите возможность [загрузки демонстрационных данных](tutorial-load-sample-data.md) для использования с несколькими пошаговыми руководствами.