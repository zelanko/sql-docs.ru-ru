---
title: Задача удаления кластера Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 839350610bdcc55d185fa06c122e71b50c5ca753
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832678"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Задача удаления кластера Azure HDInsight
**Задача удаления кластера Azure HDInsight** позволяет пакету служб SSIS удалить кластер Azure HDInsight в указанной подписке и группе ресурсов Azure.
  
> [!NOTE]
> Удаление кластера HDInsight может занимать от 10 до 20 минут.  
  
Чтобы добавить **задачу удаления кластера Azure HDInsight**, перетащите ее в конструкторе служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы вызвать диалоговое окно **Редактор задач удаления кластера Azure HDInsight** .  
  
Следующая таблица содержит описание полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Описание**|  
|AzureResourceManagerConnection|Выберите существующий или создайте новый диспетчер подключений Azure Resource Manager, который будет использоваться для удаления кластера HDInsight.|
|SubscriptionId|Укажите идентификатор подписки, в которую входит кластер HDInsight.|
|ResourceGroup|Укажите идентификатор группы ресурсов Azure, в которую входит кластер HDInsight.|
|ClusterName|Укажите имя кластера для удаления.|  
|FailIfNotExists|Укажите, следует ли завершать задачу сбоем, если кластер не существует.|
