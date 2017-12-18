---
title: "Диспетчер подключений Azure Data Lake Store | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: "7"
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 556f0efa1ce15ee23acc190e547e3700e64eca4d
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="azure-data-lake-store-connection-manager"></a>Диспетчер подключений Azure Data Lake Store
Пакет служб SQL Server Integration Services (SSIS) может использовать диспетчер подключений Azure Data Lake Store для подключения к службе Azure Data Lake Store с использованием одного из двух следующих типов проверки подлинности:
-   удостоверение пользователя Azure AD;
-   удостоверение службы Azure AD. 

Диспетчер подключений Azure Data Lake Store входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

>   [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Azure Data Lake Store), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Store

1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureDataLake** и щелкните **Добавить**. Откроется диалоговое окно **Редактор диспетчера подключений Azure Data Lake Store**.
  
2.  В диалоговом окне **Редактор диспетчера подключений Azure Data Lake Store** в поле **Узел ADLS** введите URL-адрес узла Azure Data Lake Store. Пример: `https://test.azuredatalakestore.net` или `test.azuredatalakestore.net`.
  
3.  В поле **Проверка подлинности** выберите подходящий тип проверки подлинности для доступа к данным в Azure Data Lake Store.

    1.  Если вы выбрали вариант **Удостоверение пользователя Azure AD**, выполните указанные ниже действия.
        1. Укажите значения в полях **Имя пользователя** и **Пароль**. 
    
        2. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**. Если вы или администратор клиента ранее не давали согласия на разрешение доступа к данным Azure Data Lake Store со стороны служб SSIS, выберите **Принять** при появлении соответствующего запроса. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > При выборе варианта проверки подлинности **Удостоверение пользователя Azure AD** многофакторная проверка подлинности и проверка подлинности учетной записи Майкрософт не поддерживаются.
    
    2. Если вы выбрали вариант **Удостоверение службы Azure AD**, выполните указанные ниже действия.
        1. Создайте приложение и субъект-службу Azure Active Directory (AAD) для доступа к данным Azure Data Lake.
    
        2. Назначьте приложению AAD соответствующие разрешения на доступ к ресурсам Azure Data Lake. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Укажите значения в полях **Идентификатор клиента**, **Секретный ключ** и **Имя клиента**.
    
        4. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**.  
  
6.  Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Редактор диспетчера подключений Azure Data Lake Store**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Просмотр свойств диспетчера подключений
Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
