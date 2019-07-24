---
title: Развертывание SQL Server кластера больших данных с помощью Azure Data Studio записных книжек
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для развертывания кластера больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f12a4f06ceb1c3a48b2b2fc661c59594e6d6cce3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426424"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Развертывание SQL Server кластера больших данных с помощью Azure Data Studio записных книжек

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]предоставляет расширение для Azure Data Studio, включающее записные книжки развертывания. Записная книжка развертывания содержит документацию и код, которые можно использовать в Azure Data Studio для создания SQL Server кластера больших данных. 

Изначально реализована как проект с открытым исходным кодом, в [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)реализованы [записные книжки](notebooks-guidance.md) . Markdown можно использовать для текста в текстовых ячейках и в одном из доступных ядер для написания кода в ячейках кода.

Для развертывания кластеров [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]больших данных можно использовать записные книжки.

## <a name="prerequisites"></a>Предварительные требования
Для запуска записной книжки требуются следующие необходимые компоненты:

* Установлена последняя версия [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]расширение, установленное в Azure Data Studio

Кроме того, для развертывания кластера больших данных SQL Server 2019 требуется:

* [аздата](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Запуск записной книжки

1. Установите и запустите [сборку "предварительные оценки" Azure Data Studio](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master).
1.  На вкладке **подключения** щелкните **...** и выберите **развернуть SQL Server кластер больших данных.** ...

   ![AI и ML](media/deploy-notebooks/deploy-notebooks-1.png)

1. В **целевом объекте развертывания**в **разделе Параметры**выберите **новый кластер Azure Kubernetes** или **существующий кластер службы Kubernetes Azure**.
1. Выберите **открыть записную книжку**.

Это действие запускает соответствующую записную книжку. Чтобы завершить развертывание, следуйте инструкциям в записной книжке, чтобы развернуть кластер больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] в существующем или новом кластере службы Azure Kubernetes.
