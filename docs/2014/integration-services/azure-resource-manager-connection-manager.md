---
title: Диспетчер подключений Azure Resource Manager | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3e2535d1d0b05cd89fc2648c0be858fbe77ea2eb
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460539"
---
# <a name="azure-resource-manager-connection-manager"></a>Диспетчер подключений Azure Resource Manager
**Диспетчер подключений Azure Resource Manager** позволяет пакету служб SSIS управлять ресурсами Azure с помощью [субъекта-службы](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Чтобы создать и настроить **диспетчер подключений Azure Resource Manager**, выполните указанные ниже действия:

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureResourceManager**и щелкните **Добавить**.
2. В диалоговом окне **редактора диспетчера подключений Azure Resource Manager** укажите **Идентификатор приложения**, **Ключ приложения** и **Идентификатор клиента** для субъекта-службы. Дополнительные сведения об этих свойствах см. [этой](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) статье.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .
