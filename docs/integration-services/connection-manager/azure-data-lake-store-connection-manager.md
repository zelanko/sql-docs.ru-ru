---
title: Диспетчер подключений Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 2a8ed5e2326a5d769f190421d2427c06bc2e1211
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728373"
---
# <a name="azure-data-lake-store-connection-manager"></a>Диспетчер подключений Azure Data Lake Store

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Пакет служб SQL Server Integration Services (SSIS) может использовать диспетчер подключений Azure Data Lake Store для подключения к службе Azure Data Lake Storage 1-го поколения с использованием одного из двух следующих типов проверки подлинности:
-   удостоверение пользователя Azure AD;
-   удостоверение службы Azure AD. 

Диспетчер подключений Azure Data Lake Store входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

> [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Data Lake Storage 1-го поколения), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Store

1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureDataLake** и щелкните **Добавить**. Откроется диалоговое окно **Редактор диспетчера подключений Azure Data Lake Store**.
  
2.  В диалоговом окне **редактора диспетчера подключений Azure Data Lake Store** в поле **ADLS Host** (Узел ADLS) введите URL-адрес узла Data Lake Storage 1-го поколения. Пример: `https://test.azuredatalakestore.net` или `test.azuredatalakestore.net`.
  
3.  В поле **Проверка подлинности** выберите подходящий тип проверки подлинности для получения доступа к данным в Data Lake Storage 1-го поколения.

    1.  Если вы выбрали вариант **Удостоверение пользователя Azure AD**, выполните указанные ниже действия.
        1. Укажите значения в полях **Имя пользователя** и **Пароль**. 
    
        2. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**. Если вы или администратор клиента ранее не давали согласия на разрешение доступа к данным Data Lake Storage 1-го поколения со стороны служб SSIS, выберите **Принять** при появлении соответствующего запроса. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        > [!NOTE] 
        > При выборе варианта проверки подлинности **Удостоверение пользователя Azure AD** многофакторная проверка подлинности и проверка подлинности учетной записи Майкрософт не поддерживаются.
    
    2. Если вы выбрали вариант **Удостоверение службы Azure AD**, выполните указанные ниже действия.
        1. Создайте приложение и субъект-службу Azure Active Directory (AAD) для доступа к данным Azure Data Lake Storage 1-го поколения.
    
        2. Назначьте приложению AAD соответствующие разрешения на доступ к ресурсам Azure Data Lake Storage 1-го поколения. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Укажите значения в полях **Идентификатор клиента**, **Секретный ключ** и **Имя клиента**.
    
        4. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**.  
  
6.  Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Редактор диспетчера подключений Azure Data Lake Store**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Просмотр свойств диспетчера подключений
Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
