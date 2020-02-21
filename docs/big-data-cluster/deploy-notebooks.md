---
title: Развертывание. Записная книжка Azure Data Studio
titleSuffix: SQL Server Big Data Clusters
description: Используйте записную книжку из Azure Data Studio для развертывания кластера больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e11a4ac0bcbb66d6b3216d8c2f7a4a3b15cedfb8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75246869"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebook"></a>Развертывание кластера больших данных SQL Server с помощью записной книжки Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки для развертывания. Записная книжка для развертывания содержит документацию и код, которые можно использовать в Azure Data Studio для создания кластеров больших данных SQL Server.

[Записные книжки](notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь интегрированы в [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="prerequisites"></a>Предварительные требования

Для запуска записной книжки требуются следующие компоненты:

* Последняя [сборка Azure Data Studio для участников программы предварительной оценки](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)

Помимо перечисленных выше компонентов, для развертывания кластера больших данных SQL Server 2019 требуется следующее:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI (при развертывании в Azure)](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

## <a name="launch-the-notebook"></a>Запуск записной книжки

1. Запустите Azure Data Studio.

2. На вкладке **Подключения** нажмите на многоточие ( **...** ) и выберите параметр **Развернуть SQL Server...** .

   ![Развертывание SQL Server](media/deploy-notebooks/deploy-notebooks.png)

3. В параметрах развертывания выберите **Кластер больших данных SQL Server**.

4. В разделе**Параметры** **целевого объекта развертывания** выберите **новый кластер Azure Kubernetes** или **существующий кластер службы Azure Kubernetes**.

5. Принятие условий соглашения о конфиденциальности и лицензии

6. Это диалоговое окно также проверяет, существуют ли на узле средства, необходимые для выбранного типа развертывания SQL. Кнопка **Выбрать** активируется только после того, как проверка инструментов будет выполнена успешно.

7. Нажмите кнопку **Выбрать**. Это действие запускает процесс развертывания.

## <a name="set-deployment-configuration-template"></a>Настройка шаблона конфигурации развертывания

Чтобы настроить параметры профиля развертывания, выполните приведенные ниже инструкции.

### <a name="target-configuration-template"></a>Целевой шаблон конфигурации

Выберите целевой шаблон конфигурации из доступных шаблонов. Доступность профилей зависит от типа целевого объекта развертывания, выбранного в предыдущем диалоговом окне.

   ![Шаблон конфигурации развертывания: шаг 1](media/deploy-notebooks/deployment-configuration-template.png)

### <a name="azure-settings"></a>Параметры Azure

Если целевым объектом развертывания является новая AKS, для создания кластера AKS потребуются дополнительные данные, такие как идентификатор подписки Azure, группа ресурсов, имя кластера AKS, число виртуальных машин, размер и другие дополнительные сведения.

   ![Параметры Azure](media/deploy-notebooks/azure-settings.png)

Если целевым объектом развертывания является существующий кластер Kubernetes, мастер запрашивает путь к файлу конфигурации *KUBE*, чтобы импортировать параметры кластера Kubernetes. Убедитесь, что выбран тот контекст кластера, в котором можно развернуть кластер больших данных SQL Server 2019.

   ![Контекст целевого кластера](media/deploy-notebooks/target-cluster-context.png)

### <a name="cluster-docker-and-ad-settings"></a>Параметры кластера, Docker и Active Directory

1. Введите имя кластера для BDC SQL Server 2019, а также имя пользователя и пароль администратора.
Примечание. Для контроллера и SQL Server используется одна и та же учетная запись.

   ![Параметры кластера](media/deploy-notebooks/cluster-settings.png)

2. Введите необходимые параметры Docker

   ![Параметры Docker](media/deploy-notebooks/docker-settings.png)

3. Если доступна проверка подлинности Active Directory, введите параметры Active Directory

   ![Параметры Active Directory](media/deploy-notebooks/active-directory-settings.png)

### <a name="service-settings"></a>Параметры службы

На этом экране отображаются входные данные для различных параметров, таких как **Масштабирование**, **Конечные точки**, **Хранилище** и **Дополнительные параметры хранилища**. Введите соответствующие значения и нажмите **Далее**.

#### <a name="scale-settings"></a>Настройки масштабирования

Введите количество экземпляров каждого компонента в кластере больших данных.

Экземпляр Spark можно добавить вместе с HDFS. Он добавляется в пул носителей или используется отдельно в пуле Spark.

   ![Параметры службы](media/deploy-notebooks/service-settings.png)

Дополнительные сведения о каждом из этих компонентов см. в разделе о [главном экземпляре](concept-master-instance.md), [пуле данных](concept-data-pool.md), [пуле носителей](concept-storage-pool.md) или [пуле вычислений](concept-compute-pool.md).

#### <a name="endpoint-settings"></a>Параметры конечных точек

Конечные точки по умолчанию задаются автоматически. Однако при необходимости их можно изменить.

   ![Параметры конечных точек](media/deploy-notebooks/endpoint-settings.png)

#### <a name="storage-settings"></a>Параметры хранилища

Параметры хранилища включают класс хранения и размер утверждения для данных и журналов. Данные параметры можно применять к хранилищу, данным и главному пулу SQL Server.

   ![Параметры хранилища](media/deploy-notebooks/storage-settings.png)

#### <a name="advanced-storage-settings"></a>Дополнительные параметры хранилища

Дополнительные параметры хранилища можно добавить в разделе **Дополнительные параметры хранилища**

* Пул носителей (HDFS)
* Пул данных
* SQL Server Master

   ![Дополнительные параметры хранилища](media/deploy-notebooks/advanced-storage-settings.png)

### <a name="summary"></a>Сводка

На этом экране перечисляются все входные данные, предоставленные для развертывания кластера больших данных SQL Server 2019. Файлы конфигурации можно скачать с помощью кнопки **Сохранить файлы конфигурации**. Выберите **Вывести скрипт в записную книжку**, чтобы сохранить скрипт для всей конфигурации развертывания в записной книжке. Открыв приложение Notebook, выберите команду **Выполнить ячейки**, чтобы начать развертывание BDC SQL Server 2019 в выбранном целевом объекте.

   ![Сводка](media/deploy-notebooks/deploy-sql-server-big-data-cluster-on-a-new-AKS-cluster.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о развертывании см. в [руководстве по развертыванию кластеров больших данных SQL Server](deployment-guidance.md).
