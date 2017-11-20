---
title: "Справочник по языку служб интеграции | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
ms.assetid: c67b72f1-0a1e-42f0-878a-84e85efc915b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9fe4120f8a5dc93517e8eb35b13e7fe5252be6b6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="integration-services-language-reference"></a>Справочник по языку служб Integration Services
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается API-интерфейс [!INCLUDE[tsql](../includes/tsql-md.md)] для администрирования проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], которые развернуты на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] сохраняют объекты, настройки и рабочие данные в базе данных, которая называется каталогом [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Имя по умолчанию [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] каталога является SSISDB. Объекты, которые хранятся в каталоге, включают проекты, пакеты, параметры, среды и журнал операций.  
  
 В каталоге служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] данные хранятся во внутренних таблицах, невидимых для пользователей. Однако к требуемым сведениям можно получить доступ через ряд общедоступных представлений, выполнив к ним запросы. База данных также содержит ряд хранимых процедур, которые могут использоваться для выполнения типичных задач, связанных с каталогом.  
  
 Как правило, управление объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в каталоге осуществляется путем открытия среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Однако можно также непосредственно использовать представления базы данных и хранимые процедуры или написать пользовательский код, который вызывает управляемый API. Среда [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и управляемый API запрашивают представления и вызывают хранимые процедуры, описанные в этом разделе, для выполнения многих своих задач.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Представления &#40; каталог служб Integration Services &#41;](../integration-services/system-views/views-integration-services-catalog.md)  
 Запросы к представлениям позволяют получить доступ к объектам, настройкам и рабочим данным служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 [Хранимые процедуры &#40; каталог служб Integration Services &#41;](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
 Вызовы хранимых процедур позволяют добавлять, удалять и изменять объекты и параметры служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 [Функции (каталог служб Integration Services)](http://msdn.microsoft.com/library/9f2aec85-3d4c-415f-b1f8-8328a60b1c7f)  
 Вызывайте функции для администрирования проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
  

