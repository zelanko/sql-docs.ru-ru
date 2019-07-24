---
title: Управление SQL Server кластером больших данных с помощью Azure Data Studio записных книжек
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для управления кластером больших данных и устранения неполадок.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8d87b09878539cccd40191d870bf97487579dca2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426404"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Управление кластерами больших данных для SQL Server с помощью Azure Data Studio записных книжек

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]предоставляет расширение для Azure Data Studio, включающее записные книжки развертывания. Записная книжка развертывания содержит документацию и код, которые можно использовать в Azure Data Studio для управления кластерами больших данных для SQL Server.

Изначально реализована как проект с открытым исходным кодом, в [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)реализованы [записные книжки](notebooks-guidance.md) . Markdown можно использовать для текста в текстовых ячейках и в одном из доступных ядер для написания кода в ячейках кода.

Для развертывания кластеров [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]больших данных можно использовать записные книжки.

## <a name="prerequisites"></a>Предварительные требования

Для запуска записной книжки требуются следующие необходимые компоненты:

* Последняя версия [сборки Azure Data Studio для участников программы предварительной оценки](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]расширение, установленное в Azure Data Studio

Кроме того, для развертывания кластера больших данных SQL Server 2019 требуется:

* [аздата](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)
