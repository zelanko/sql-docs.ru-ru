---
description: Диспетчер подключений Azure Resource Manager
title: Диспетчер подключений Azure Resource Manager | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 84b9c97935d0bcf89a4741304bb9a1e6b3576605
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130132"
---
# <a name="azure-resource-manager-connection-manager"></a>Диспетчер подключений Azure Resource Manager

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


**Диспетчер подключений Azure Resource Manager** позволяет пакету служб SSIS управлять ресурсами Azure с помощью [субъекта-службы](/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Диспетчер подключений Azure Resource Manager** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы создать и настроить **диспетчер подключений Azure Resource Manager**, выполните указанные ниже действия:

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureResourceManager** и щелкните **Добавить**.
2. В диалоговом окне **редактора диспетчера подключений Azure Resource Manager** укажите **Идентификатор приложения**, **Ключ приложения** и **Идентификатор клиента** для субъекта-службы. Дополнительные сведения об этих свойствах см. [этой](/azure/azure-resource-manager/resource-group-create-service-principal-portal) статье.
3. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .