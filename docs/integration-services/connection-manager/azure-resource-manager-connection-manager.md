---
title: "Диспетчер соединений диспетчер ресурсов Azure | Документы Microsoft"
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
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd1dbf668bf3ac24d9d6598b0ff9e2256d897c42
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="azure-resource-manager-connection-manager"></a>Диспетчер соединений диспетчер ресурсов Azure
**Диспетчер соединений для диспетчера ресурсов Azure** позволяет пакету служб SSIS для управления ресурсами Azure с помощью [участника-службы](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Диспетчер соединений для диспетчера ресурсов Azure** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Для создания и настройки **диспетчер соединений для диспетчера ресурсов Azure**, выполните следующие действия:

1. В **Добавление диспетчера соединений служб SSIS** выберите **AzureResourceManager**и нажмите кнопку **добавить**.
2. В **редактор диспетчера соединений для диспетчера ресурсов Azure** диалоговом окне укажите **идентификатор приложения**, **ключ приложения**, и **ИД клиента** участника службы. Дополнительные сведения об этих свойствах см. [это](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) статьи.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .

