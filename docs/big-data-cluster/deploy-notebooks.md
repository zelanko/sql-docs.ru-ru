---
title: Развертывание кластера больших данных SQL Server с помощью записных книжек Azure Data Studio
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для развертывания кластера больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fb1da50fb84cbfd44aeab50a00be1c8433b3041e
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892449"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Развертывание кластера больших данных SQL Server с помощью записных книжек Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки для развертывания. Записная книжка для развертывания содержит документацию и код, которые можно использовать в Azure Data Studio для создания кластеров больших данных SQL Server.

[Записные книжки](notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь интегрированы в [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="prerequisites"></a>предварительные требования

Для запуска записной книжки требуются следующие компоненты:

* Установлена последняя версия [сборки Azure Data Studio для участников программы предварительной оценки](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)
* расширение [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], установленное в Azure Data Studio.

Помимо перечисленных выше компонентов, для развертывания кластера больших данных SQL Server 2019 требуется следующее:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Запуск записной книжки

1. Запустите Azure Data Studio участников программы предварительной оценки.

1. На вкладке **Подключения** нажмите **...** и выберите**Развернуть кластер больших данных SQL Server...** .

   ![Искусственный интеллект и машинное обучение](media/deploy-notebooks/deploy-notebooks-1.png)

1. В разделе**Параметры** **целевого объекта развертывания** выберите **новый кластер Azure Kubernetes** или **существующий кластер службы Azure Kubernetes**.

1. Нажмите кнопку **выбрать** .

1. Это действие запускает диалоговое окно для получения вводимых пользователем данных, предоставления необходимых сведений и просмотра значений по умолчанию.

1. Нажмите кнопку **открыть записную книжку** .
Это действие запускает соответствующую записную книжку. Чтобы завершить развертывание, следуйте инструкциям в записной книжке, чтобы развернуть кластер больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] в существующем или новом кластере службы Azure Kubernetes.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании см. в [руководстве по развертыванию кластеров больших данных SQL Server](deployment-guidance.md).
