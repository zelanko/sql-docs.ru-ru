---
title: Диспетчер соединений служб Analysis Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1055a76b227bbd965150a2372ac798b3c20ca8c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191671"
---
# <a name="analysis-services-connection-manager"></a>диспетчер соединений служб Analysis Services
  Диспетчер соединений служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяет пакету подключиться к серверу, на котором запущена база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , или к проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который предоставляет доступ к данным куба и измерения. При разработке пакетов в среде [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно подключиться только к проекту служб [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Во время выполнения пакеты подключаются к серверу и базе данных, где был развернут проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Обе задачи, такие как «Выполнение инструкции DDL службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » и «Обработка службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] », а также назначения, такие как «Обучение модели интеллектуального анализа данных», используют диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Дополнительные сведения о базах данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Базы данных многомерных моделей (службы SSAS)](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Настройка диспетчера соединений служб Analysis Services  
 При добавлении [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] диспетчера соединений в пакет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает соединение диспетчер, который разрешается как [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] подключения во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений `Connections` коллекцию пакета. `ConnectionManagerType` Диспетчера соединений задано значение `MSOLAP100`.  
  
 Диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно настроить следующими способами:  
  
-   Ввести строку соединения, настроенную с учетом требований поставщика Microsoft OLE для служб Analysis Services.  
  
-   Указать экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , к которому нужно подключиться.  
  
-   При подключении к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]указать метод проверки подлинности.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений служб Analysis Services"](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  