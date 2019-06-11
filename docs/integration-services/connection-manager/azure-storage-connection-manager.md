---
title: Диспетчер подключений службы хранилища Azure | Документы Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03acf5db82c21a66e2fbd8337713b6989ce36a31
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403062"
---
# <a name="azure-storage-connection-manager"></a>Диспетчер подключений службы хранилища Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

  **Диспетчер подключений службы хранилища Azure** позволяет пакету служб SSIS подключаться к учетной записи хранения Azure.
   
 **Диспетчер подключений службы хранилища Azure** входит в состав пакета дополнительных компонентов [SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureStorage**и щелкните **Добавить**.  
  
Доступны следующие свойства.

- **Служба**. Указывает службу хранилища для подключения.
- **Имя учетной записи**. Указывает имя учетной записи хранения.
- **Проверка подлинности**. Указывает используемый метод проверки подлинности. Поддерживаются методы проверки подлинности **AccessKey** и **ServicePrincipal**.
    - **AccessKey**. Для этого метода проверки подлинности укажите **ключ учетной записи**.
    - **ServicePrincipal**. Для этого метода проверки подлинности укажите **Идентификатор приложения**, **Ключ приложения** и **Идентификатор клиента** субъекта-службы.
      Следует назначить субъекту-службе роль **участник для данных хранилища BLOB-объектов** в учетной записи хранения.
      Подробности см. [здесь](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
- **Среда**. Указывает облачную среду, где размещается учетная запись хранения.
