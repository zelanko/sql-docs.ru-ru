---
description: Диспетчер подключений Azure HDInsight
title: Диспетчер подключений Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 6acb9fec83da610246001df5bc68591ecab1a225
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478057"
---
# <a name="azure-hdinsight-connection-manager"></a>Диспетчер подключений Azure HDInsight

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


**Диспетчер подключений Azure HDInsight** позволяет пакету служб SSIS подключаться к кластеру Azure HDInsight.

**Диспетчер подключений Azure HDInsight** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы создать и настроить **диспетчер подключений Azure HDInsight**, выполните указанные ниже действия.

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureHDInsight** и щелкните **Добавить**.
2. В диалоговом окне **Редактор диспетчера подключений Azure HDInsight** укажите **DNS-имя кластера** (без префикса протокола), **имя пользователя** и **пароль** для кластера HDInsight, к которому необходимо подключиться.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .
