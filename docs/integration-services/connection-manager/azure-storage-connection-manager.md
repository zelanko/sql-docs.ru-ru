---
title: Диспетчер подключений службы хранилища Azure | Документация Майкрософт
description: Диспетчер подключений службы хранилища Azure позволяет пакету служб SSIS подключаться к учетной записи хранения Azure.
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 44193053e6a5f09b2864b95ded9c5ac933c4cf95
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726025"
---
# <a name="azure-storage-connection-manager"></a>Диспетчер подключений службы хранилища Azure

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Диспетчер подключений службы хранилища Azure позволяет пакету служб SQL Server Integration Services (SSIS) подключаться к учетной записи хранения Azure. Диспетчер подключений службы хранилища Azure входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureStorage** > **Добавить**.  
  
Доступны следующие свойства:

- **Служба**. Указывает службу хранилища для подключения.
- **Имя учетной записи**. Указывает имя учетной записи хранения.
- **Проверка подлинности**. Указывает используемый метод проверки подлинности. Поддерживаются методы проверки подлинности AccessKey, ServicePrincipal и SharedAccessSignature
    - **AccessKey**. Для этого метода проверки подлинности укажите **ключ учетной записи**.
    - **ServicePrincipal**. Для этого метода проверки подлинности укажите **идентификатор приложения**, **ключ приложения** и **идентификатор клиента** субъекта-службы.
      Для работы **тестового подключения** субъекту-службе следует назначить по крайней мере роль **Модуль чтения данных BLOB-объектов хранилища** в учетной записи хранения.
      Дополнительные сведения см. в статье о [предоставлении доступа к данным больших двоичных объектов и очереди с помощью ролей RBAC на портале Azure](/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
    - **SharedAccessSignature**. Для этого метода проверки подлинности укажите по меньшей мере **Token** подписанного URL-адреса.
      Чтобы проверить подключение, дополнительно укажите область ресурсов, используемую для проверки. Это может быть **служба**, **контейнер** или **BLOB-объект**.
      Для **контейнера** и **BLOB-объекта** укажите имя контейнера и путь к BLOB-объекту соответственно.
      Дополнительные сведения см. в статье [Общие сведения о подписанном URL-адресе службы хранилища Azure](/azure/storage/common/storage-sas-overview).
- **Среда**. Указывает облачную среду, где размещается учетная запись хранения.

## <a name="managed-identities-for-azure-resources-authentication"></a>Управляемые удостоверения для проверки подлинности ресурсов Azure
При выполнении пакетов SSIS в [среде Azure-SSIS Integration Runtime Фабрики данных Azure](/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) вы можете использовать [управляемое удостоверение](/azure/data-factory/connector-azure-sql-database#managed-identity), связанное с вашей фабрикой данных, для проверки подлинности хранилища Azure. С помощью этого удостоверения назначенная фабрика может обращаться к данным и копировать их из вашей учетной записи хранения или в нее.

Общие сведения о проверке подлинности хранилища Azure см. в статье [Authenticate access to Azure Storage using Azure Active Directory](/azure/storage/common/storage-auth-aad) (Проверка подлинности при доступе к службе хранилища Azure с помощью Azure Active Directory). Чтобы использовать для службы хранилища Azure аутентификацию, выполняемую с помощью управляемого удостоверения, сделайте следующее:

1. [Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](/azure/data-factory/data-factory-service-identity). Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор приложения управляемого удостоверения** (не **идентификатор объекта управляемого удостоверения**).

1. Предоставьте управляемому удостоверению соответствующее разрешение в учетной записи хранения. Дополнительные сведения о ролях см. в статье об [управление правами доступа к данным службы хранилища Azure с помощью RBAC](/azure/storage/common/storage-auth-aad-rbac-portal).

    - В Системе управления идентификацией и доступом (IAM) назначьте **источнику** по крайней мере роль **Модуль чтения данных BLOB-объектов хранилища**.
    - В Системе управления идентификацией и доступом (IAM) назначьте **назначению** по крайней мере роль **Участник для данных BLOB-объектов хранилища**.

Затем настройте проверку подлинности с использованием управляемого удостоверения для диспетчера подключений хранилища Azure. Это можно сделать такими способами:

- **Настройка во время разработки.** В конструкторе SSIS дважды щелкните диспетчер подключений к хранилищу Azure, чтобы открыть **редактор диспетчера подключений хранилища Azure**. Выберите **Use managed identity to authenticate on Azure** (Использовать управляемое удостоверение для проверки подлинности в Azure).
    > [!NOTE]
    >  Сейчас это свойство не оказывает никакого влияния (т. е. проверка подлинности с помощью управляемого удостоверения не работает) при выполнении пакета SSIS в конструкторе SSIS или [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
- **Настройка во время выполнения.** При выполнении пакета с помощью [SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md) или [действия "Выполнить пакет SSIS" Фабрики данных Azure](/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) найдите диспетчер подключений хранилища Azure. Установите для его свойства `ConnectUsingManagedIdentity` значение `True`.
    > [!NOTE]
    >  В среде Azure-SSIS Integration Runtime все остальные методы проверки подлинности (например, ключ доступа и субъект-служба), предварительно настроенные в диспетчере подключений хранилища Azure, переопределяются, если для операций с хранилищем используется проверка подлинности с помощью управляемого удостоверения.

> [!NOTE]
>  Чтобы настроить проверку подлинности с помощью управляемого удостоверения для существующих пакетов, рекомендуем как минимум однократно перестроить проект SSIS с использованием [конструктора SSIS последней версии](../../ssdt/download-sql-server-data-tools-ssdt.md). Повторно разверните этот проект служб SSIS в среде Azure-SSIS Integration Runtime, чтобы новое свойство `ConnectUsingManagedIdentity` диспетчера подключений автоматически добавилось во все диспетчеры подключений хранилища Azure в проекте SSIS. Кроме того, можно непосредственно переопределить свойство, указав при выполнении путь **\Package.Connections[{имя_диспетчера_подключений}].Properties[ConnectUsingManagedIdentity]** .

## <a name="secure-network-traffic-to-your-storage-account"></a>Защита сетевого трафика в учетной записи хранения
Фабрика данных Azure теперь является [доверенной службой Майкрософт](/azure/storage/common/storage-network-security#trusted-microsoft-services) для службы хранилища Azure. При использовании проверки подлинности на основе управляемого удостоверения можно защитить учетную запись хранения, [предоставив доступ к выбранным сетям](/azure/storage/common/storage-network-security#change-the-default-network-access-rule), в то же время предоставив фабрике данных доступ к вашей учетной записи. Инструкции см. в разделе об [управлении исключениями](/azure/storage/common/storage-network-security#managing-exceptions).

## <a name="see-also"></a>См. также раздел  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)