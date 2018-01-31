---
title: "Диспетчер подключений Azure Resource Manager | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b00b3556469d9f35e4edd7365b214a0b17b79e61
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="azure-resource-manager-connection-manager"></a>Диспетчер подключений Azure Resource Manager
**Диспетчер подключений Azure Resource Manager** позволяет пакету служб SSIS управлять ресурсами Azure с помощью [субъекта-службы](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Диспетчер подключений Azure Resource Manager** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы создать и настроить **диспетчер подключений Azure Resource Manager**, выполните указанные ниже действия:

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureResourceManager**и щелкните **Добавить**.
2. В диалоговом окне **редактора диспетчера подключений Azure Resource Manager** укажите **Идентификатор приложения**, **Ключ приложения** и **Идентификатор клиента** для субъекта-службы. Дополнительные сведения об этих свойствах см. [этой](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) статье.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .
