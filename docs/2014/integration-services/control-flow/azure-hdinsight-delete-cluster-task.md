---
title: Задача удаления кластера Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 42a7a3d89d4f8c939e097cdb9016f2be7b0e35d7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193618"
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