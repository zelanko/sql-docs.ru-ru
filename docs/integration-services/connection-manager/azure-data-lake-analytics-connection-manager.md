---
title: Диспетчер подключений Azure Data Lake Analytics | Документация Майкрософт
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 17b63aad55cf50262d7e1e56267859b1a34cc9d3
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854428"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Диспетчер подключений Azure Data Lake Analytics

Пакет SQL Server Integration Services (SSIS) может использовать диспетчер подключений Azure Data Lake Analytics для подключения к учетной записи Azure Data Lake Analytics с использованием одного из двух следующих типов аутентификации:
-   удостоверение пользователя Azure AD;
-   удостоверение службы Azure AD. 

Диспетчер подключений Azure Data Lake Analytics входит в состав [пакета дополнительных компонентов SSIS для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
## <a name="configure-the-azure-data-lake-analytics-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Analytics

1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureDataLakeAnalytics** и щелкните **Добавить**. Откроется диалоговое окно **редактора диспетчера подключений Azure Data Lake Analytics**.
  
2.  В диалоговом окне **редактора диспетчера подключений Azure Data Lake Analytics** введите в поле **Имя учетной записи ADLS** соответствующее имя для Azure Data Lake Analytics. Например, myadlaaccountname.
  
3.  В поле **Проверка подлинности** выберите подходящий тип проверки подлинности для доступа к данным в Azure Data Lake Analytics.

    1.  Если вы выбрали вариант **Удостоверение пользователя Azure AD**, выполните указанные ниже действия.
        1. Укажите значения в полях **Имя пользователя** и **Пароль**. 
    
        2. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**. Если вы или администратор клиента ранее не давали согласия на доступ из SSIS к учетной записи Azure Data Lake Analytics, выберите **Принять** при появлении соответствующего запроса. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > При выборе варианта проверки подлинности **Удостоверение пользователя Azure AD** многофакторная проверка подлинности и проверка подлинности учетной записи Майкрософт не поддерживаются.
    
    2. Если вы выбрали вариант **Удостоверение службы Azure AD**, выполните указанные ниже действия.
        1. Создайте приложение и субъект-службу Azure Active Directory (AAD) для доступа к учетной записи Azure Data Lake Analytics. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        2. Назначьте приложению AAD соответствующие разрешения на доступ к учетной записи Azure Data Lake Analytics. Узнайте, как предоставить права доступа к учетной записи Azure Data Lake Analytics [с помощью мастера добавления пользователей](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user). 
    
        3. Укажите значения для полей **Идентификатор приложения**, **Ключ проверки подлинности** и **Идентификатор клиента**.
    
        4. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**.  

4.  Щелкните **ОК**, чтобы закрыть диалоговое окно **редактора диспетчера подключений Azure Data Lake Analytics**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Просмотр свойств диспетчера подключений
Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
