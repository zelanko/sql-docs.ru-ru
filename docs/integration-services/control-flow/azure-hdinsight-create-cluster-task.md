---
title: "Azure HDInsight задача создания кластера | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71a24dc15253916c32b07e6024e2ab32514c9d39
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-create-cluster-task"></a>Задача создания кластера Azure HDInsight
**Задача создания кластера Azure HDInsight** позволяет пакету служб SSIS для создания кластера Azure HDInsight в указанной Azure группы ресурса и подписки.
  
**Задача создания кластера Azure HDInsight** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]  
> - Создание нового кластера HDInsight может занять 10 ~ 20 минут.  
> - Нет затраты, связанные с созданием и под управлением кластера Azure HDInsight. В разделе [цены на HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/) подробные сведения.  
  
Чтобы добавить **задачу создания кластера Azure HDInsight**, перетащите ее в конструктор служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите пункт **Изменить** , чтобы вызвать диалоговое окно **Azure HDInsight Create Cluster Task Editor** (Редактор задач создания кластера Azure HDInsight).  
  
Ниже приводится описание полей в этом окне.  
  
|||  
|-|-|  
|**Поле**|**Description**|  
|AzureResourceManagerConnection|Выберите существующий диспетчер соединений диспетчер ресурсов Azure или создайте новый, который будет использоваться для создания кластера HDInsight.|  
|AzureStorageConnection|Выберите существующий диспетчер подключений службы хранилища Azure или создайте диспетчер подключений, который ссылается на учетную запись хранения Azure, которая будет связана с кластером HDInsight.|
|Идентификатор подписки|Укажите идентификатор подписки, в которой будет создан кластер HDInsight.|
|Группа ресурсов|Укажите, будет создан в кластер HDInsight группы ресурсов Azure.|
|Местоположение|Определите расположение кластера HDInsight. Кластера должны создаваться в том же расположении, что указанную учетную запись хранения Azure.|  
|ClusterName|Укажите имя для создаваемого кластера HDInsight.|  
|ClusterSize|Укажите количество узлов для создания кластера.|  
|BlobContainer|Укажите имя контейнера хранилища по умолчанию, следует связать с кластером HDInsight.|  
|UserName|Укажите имя пользователя, используемое для подключения к кластеру HDInsight.|  
|Пароль|Укажите пароль, используемый для подключения к кластеру HDInsight.|
|SshUserName|Укажите имя пользователя, используемое для удаленного доступа к кластеру HDInsight с помощью SSH.|
|SshPassword|Укажите пароль, используемый для удаленного доступа к кластеру HDInsight с помощью SSH.|
|FailIfExists|Укажите, следует ли завершать задачу сбоем, если кластер уже существует.|  
  
> [!NOTE]  
> Расположение кластера HDInsight и учетной записи хранилища Azure должны быть одинаковыми.

