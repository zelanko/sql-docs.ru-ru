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
ms.openlocfilehash: f171499471f8f94ad970446d31cf796f4ab55fb7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028771"
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
      Для работы **тестового подключения** субъекту-службе следует назначить по крайней мере роль **Читатель данных в хранилище BLOB-объектов** в учетной записи хранения.
      Подробности см. [здесь](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
- **Среда**. Указывает облачную среду, где размещается учетная запись хранения.

## <a name="managed-identities-for-azure-resources-authentication"></a>Управляемые удостоверения для проверки подлинности ресурсов Azure
При выполнении пакетов SSIS в [среде Azure-SSIS Integration Runtime Фабрики данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) вы можете использовать [управляемое удостоверение](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), связанное с вашей фабрикой данных, для проверки подлинности хранилища Azure. С помощью этого удостоверения назначенная фабрика может обращаться к данным и копировать их из вашей учетной записи хранения или в нее.

Общие сведения о проверке подлинности хранилища Azure см. в статье [Authenticate access to Azure Storage using Azure Active Directory](https://docs.microsoft.com/azure/storage/common/storage-auth-aad) (Проверка подлинности при доступе к службе хранилища Azure с помощью Azure Active Directory). Чтобы использовать проверку подлинности с помощью управляемого удостоверения для хранилища Azure, настройте учетную запись хранения, сделав следующее:

1. **[Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор приложения управляемого удостоверения** (не **идентификатор объекта управляемого удостоверения**).

1. **Предоставьте управляемому удостоверению правильное разрешение в учетной записи хранения.** Дополнительные сведения о ролях см. в статье [Manage access rights to Azure Storage data with RBAC](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal) (Управление ролями доступа к данным службы хранилища Azure с помощью RBAC).

    - **Для источника** в Системе управления идентификацией и доступом (IAM) предоставьте по крайней мере роль **читателя данных Storage Blob**.
    - **Для назначения** в системе управления идентификацией и доступом предоставьте по крайней мере роль **участника данных Storage Blob**.

Затем **настройте проверку подлинности с помощью управляемого удостоверения** для диспетчера подключений хранилища Azure. Это можно сделать двумя способами.

1. Настройка во время разработки. В конструкторе SSIS дважды щелкните диспетчер подключений к хранилищу Azure, чтобы **открыть редактор диспетчера подключений хранилища Azure** и установите флажок **Use managed identity to authenticate on Azure** (Использовать управляемое удостоверение для проверки подлинности в Azure).
    > [!NOTE]
    >  Сейчас это свойство НЕ оказывает никакого влияния (т. е. проверка подлинности с помощью управляемого удостоверения не работает) при выполнении пакета SSIS в конструкторе SSIS или [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Настройка во время выполнения. При выполнении пакета с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) или [действия "Выполнить пакет SSIS" Фабрики данных Azure ](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) найдите диспетчер подключений к хранилищу Azure и измените значение его свойства **ConnectUsingManagedIdentity** на **True**.
    > [!NOTE]
    >  В среде Azure-SSIS Integration Runtime все остальные методы проверки подлинности (например, ключ доступа, субъект-служба), предварительно настроенные в диспетчере подключений хранилища Azure, **переопределяются**, когда для операций с хранилищем используется проверка подлинности с помощью управляемого удостоверения.

> [!NOTE]
>  Чтобы настроить проверку подлинности с помощью управляемого удостоверения для существующих пакетов, рекомендуется хотя бы раз перестроить проект SSIS с использованием [последнего конструктора SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) и повторно развернуть этот проект в среде выполнения интеграции Azure-SSIS. Так новое свойство диспетчера подключений **ConnectUsingManagedIdentity** будет автоматически добавлено во все диспетчеры подключений хранилища Azure в проекте SSIS. Альтернативный способ — напрямую использовать переопределение свойства, указав при выполнении путь к свойству **\Package.Connections[{имя_диспетчера_подключений}].Properties[ConnectUsingManagedIdentity]**

## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)
