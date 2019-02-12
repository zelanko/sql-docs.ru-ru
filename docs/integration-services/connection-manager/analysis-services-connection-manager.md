---
title: Диспетчер соединений служб Analysis Services | Документы Майкрософт
ms.custom: ''
ms.date: 01/25/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d999079c7c2f5de55704fed602c2c5047444f588
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012955"
---
# <a name="analysis-services-connection-manager"></a>диспетчер соединений служб Analysis Services
  Диспетчер соединений служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяет пакету подключиться к серверу, на котором запущена база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , или к проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который предоставляет доступ к данным куба и измерения. При разработке пакетов в среде [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно подключиться только к проекту служб [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Во время выполнения пакеты подключаются к серверу и базе данных, где был развернут проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Обе задачи, такие как «Выполнение инструкции DDL службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » и «Обработка службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] », а также назначения, такие как «Обучение модели интеллектуального анализа данных», используют диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Дополнительные сведения о базах данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Базы данных многомерных моделей (службы SSAS)](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Настройка диспетчера соединений служб Analysis Services  
 Если добавить к пакету диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , устанавливает свойства диспетчера соединений и добавляет диспетчер соединений в коллекцию **Соединения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **MSOLAP100**.  
  
 Диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно настроить следующими способами:  
  
-   Ввести строку соединения, настроенную с учетом требований поставщика Microsoft OLE для служб Analysis Services.  
  
-   Указать экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , к которому нужно подключиться.  
  
-   При подключении к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]указать метод проверки подлинности.  

> [!NOTE]    
>  Если вы используете SSIS в Фабрике данных Azure (ADF) и хотите подключиться к экземпляру служб Azure Analysis Services (AAS), нужно использовать не учетную запись с многофакторной идентификацией (MFA), а субъект-службу или учетную запись, которая не требует взаимодействия или MFA. Инструкции по созданию такой учетной записи и назначению ей роли администратора сервера см. [здесь](https://docs.microsoft.com/azure/analysis-services/analysis-services-service-principal). Затем выберите **Использовать указанные имя пользователя и пароль** для входа на сервер в диспетчере подключений и, наконец, введите `User name: app:YourApplicationID` и `Password: YourAuthorizationKey`.
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Добавление диалогового окна  «Диспетчер соединений со службами Analysis Services" в справочник по пользовательскому интерфейсу](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  
