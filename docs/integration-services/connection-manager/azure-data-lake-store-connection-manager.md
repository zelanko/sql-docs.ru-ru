---
title: "Диспетчер соединений для хранилища Озера данных Azure | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
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
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 0a84b10114d785c9216a0902b2eefbcb0bd3f4c8
ms.contentlocale: ru-ru
ms.lasthandoff: 10/11/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Диспетчер подключений Azure Data Lake Store
Пакет служб SQL Server Integration Services (SSIS) можно использовать диспетчер соединений для хранилища Озера данных Azure для подключения к службе хранилища Озера данных Azure с одним из двух следующих типов проверки подлинности:
-   Удостоверение пользователя Azure AD
-   Удостоверение службы Azure AD 

Диспетчер соединений для хранилища Озера данных Azure — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

>   [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Azure Data Lake Store), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Store

1.  В **Добавление диспетчера соединений служб SSIS** выберите **AzureDataLake**, а затем выберите **добавить**. **Редактор диспетчера соединений хранилища Озера данных Azure** откроется диалоговое окно.
  
2.  В **редактор диспетчера соединений хранилища Озера данных Azure** диалогового **ADLS узла** укажите URL-адрес узла хранилища Озера данных Azure. Например: `https://test.azuredatalakestore.net` или `test.azuredatalakestore.net`.
  
3.  В **проверки подлинности** выберите тип проверки подлинности для доступа к данным в хранилище Озера данных Azure.

    1.  При выборе **удостоверение пользователя Azure AD** проверки подлинности, то выполните следующие действия:
        1. Укажите значения для **имя пользователя** и **пароль** поля. 
    
        2. Чтобы проверить соединение, выберите **проверить подключение**. Если пользователь или администратор клиента не соглашается ранее разрешить служб SSIS получить доступ к данным хранилища Озера данных Azure, выберите **Accept** при появлении запроса. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > При выборе **удостоверение пользователя Azure AD** вариант проверки подлинности, многофакторная проверка подлинности и проверка подлинности учетной записи Майкрософт не поддерживается.
    
    2. При выборе **удостоверение службы Azure AD** проверки подлинности, то выполните следующие действия:
        1. Создание приложения Azure Active Directory (AAD) и службы участника для доступа к данным Озера данных Azure.
    
        2. Назначьте соответствующие разрешения для этого приложения AAD, которые имеют доступ к ресурсам Озера данных Azure. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Укажите значения для **идентификатор клиента**, **секретный ключ**, и **имя клиента** поля.
    
        4. Чтобы проверить соединение, выберите **проверить подключение**.  
  
6.  Выберите **ОК** закрыть **редактор диспетчера соединений хранилища Озера данных Azure** диалоговое окно.  

## <a name="view-the-properties-of-the-connection-manager"></a>Просмотр свойств диспетчера соединений
Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
