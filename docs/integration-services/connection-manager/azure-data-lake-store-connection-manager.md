---
title: "Диспетчер соединений для хранилища Озера данных Azure | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: 39630087acdb2ade2e77d4364e4467f8d740d8d4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Диспетчер подключений Azure Data Lake Store
  **Диспетчер подключений Azure Data Lake Store** позволяет пакету служб SSIS подключаться к службе Azure Data Lake Store с помощью двух типов проверки подлинности: удостоверение пользователя Azure AD и удостоверение службы Azure AD.  
  
 **Диспетчер подключений хранилища Озера данных Azure** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

>   [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Azure Data Lake Store), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Store

 
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureDataLake**и щелкните **Добавить**.  
  
2.  В диалоговом окне "Редактор диспетчера подключений Azure Data Lake Store" введите URL-адрес узла Azure Data Lake Store в поле **Узел ADLS** . Например: `https://test.azuredatalakestore.net` или `test.azuredatalakestore.net`.
  
3.  Выберите соответствующий тип проверки подлинности для доступа к данным Azure Data Lake Store.

    1.  Если вы выбрали вариант **удостоверение пользователя Azure AD** , выполните следующие действия.
        1. Укажите значения в полях **Имя пользователя** и **Пароль** . 
    
        2. Щелкните **Проверить подключение** для проверки подключения. Если вы ранее не согласовали доступ служб SSIS к данным Azure Data Lake Store с администратором клиента, во всплывающем диалоговом окне нажмите кнопку **Принять** , чтобы разрешить службам SSIS доступ к данным Azure Data Lake Store. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > При выборе параметра проверки подлинности "Удостоверение пользователя Azure AD" многофакторная проверка подлинности и учетная запись Майкрософт НЕ поддерживаются.
    
    2. Если вы выбрали вариант **удостоверение службы Azure AD** , выполните следующие действия.
        1. Создайте приложение AAD и субъект-службу, которые могут получать доступ к ресурсам Azure Data Lake.
    
        2. Назначьте приложению AAD соответствующие разрешения. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Укажите значения в полях **Идентификатор клиента**, **Секретный ключ** и **Имя клиента** .
    
        4. Щелкните **Проверить подключение** для проверки подключения.  
  
6.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
    Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
