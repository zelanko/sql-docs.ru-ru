---
title: Задача создания кластера Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2e0d73034bc131b0cc65d475f00efd4f54612b3
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433921"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Задача создания кластера Azure HDInsight
**Задача создания кластера Azure HDInsight** позволяет пакету служб SSIS создать кластер Azure HDInsight в указанной подписке и группе ресурсов Azure.
  
> [!NOTE]  
> - Создание кластера HDInsight может занимать от 10 до 20 минут.  
> - Создание кластера Azure HDInsight и управление им сопряжено с определенными затратами. Дополнительные сведения см. в статье [Цены на HDInsight](https://azure.microsoft.com/pricing/details/hdinsight/).  
  
Чтобы добавить **задачу создания кластера Azure HDInsight**, перетащите ее в конструктор служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите пункт **Изменить** , чтобы вызвать диалоговое окно **Azure HDInsight Create Cluster Task Editor** (Редактор задач создания кластера Azure HDInsight).  
  
Следующая таблица содержит описание полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Описание**|  
|AzureResourceManagerConnection|Выберите существующий или создайте новый диспетчер подключений Azure Resource Manager, который будет использоваться для создания кластера HDInsight.|  
|AzureStorageConnection|Выберите существующий диспетчер подключений службы хранилища Azure или создайте диспетчер подключений, который ссылается на учетную запись хранения Azure, которая будет связана с кластером HDInsight.|
|SubscriptionId|Укажите идентификатор подписки, где будет создан кластер HDInsight.|
|ResourceGroup|Укажите группу ресурсов Azure, где будет создан кластер HDInsight.|
|Расположение|Определите расположение кластера HDInsight. Кластер нужно создавать в том же расположении, где находится указанная учетная запись службы хранилища Azure.|  
|ClusterName|Укажите имя для создаваемого кластера HDInsight.|  
|clusterSize (размер кластера)|Укажите число узлов, которые нужно создать в кластере.|  
|BlobContainer|Укажите имя контейнера хранилища по умолчанию, связываемого с кластером HDInsight.|  
|UserName|Укажите имя пользователя, используемое для подключения к кластеру HDInsight.|  
|Пароль|Укажите пароль, используемый для подключения к кластеру HDInsight.|
|SshUserName|Укажите имя пользователя, используемое для удаленного доступа к кластеру HDInsight с помощью SSH.|
|SshPassword|Укажите пароль, используемый для удаленного доступа к кластеру HDInsight с помощью SSH.|
|FailIfExists|Укажите, следует ли завершать задачу сбоем, если кластер уже существует.|  
  
> [!NOTE]  
> Расположения кластера HDInsight и учетной записи службы хранилища Azure должны совпадать.
