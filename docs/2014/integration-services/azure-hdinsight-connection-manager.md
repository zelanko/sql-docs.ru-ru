---
title: Диспетчер подключений Azure HDInsight | Документы Майкрософт
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
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
caps.latest.revision: 2
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 3d9486108e7f16870d2bf4e22f05b8a0a288b664
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101374"
---
# <a name="azure-hdinsight-connection-manager"></a>Диспетчер подключений Azure HDInsight
**Диспетчер подключений Azure HDInsight** позволяет пакету служб SSIS подключаться к кластеру Azure HDInsight.

Чтобы создать и настроить **диспетчер подключений Azure HDInsight**, выполните указанные ниже действия.

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureHDInsight** и щелкните **Добавить**.
2. В диалоговом окне **Редактор диспетчера подключений Azure HDInsight** укажите **DNS-имя кластера** (без префикса протокола), **имя пользователя** и **пароль** для кластера HDInsight, к которому необходимо подключиться.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .