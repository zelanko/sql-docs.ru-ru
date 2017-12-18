---
title: "Документация для разработчиков ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server Database Engine]
- Database Engine [SQL Server], development
ms.assetid: 7638f46c-9e66-48e6-9a9b-425e0b788311
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b836c6af9d5862949ec7844d7a88dbc0d349228d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="database-engine-developer-documentation"></a>Документация для разработчиков ядра СУБД
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] содержит богатый набор средств разработки, администрирования приложений баз данных и управления ими.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Основные понятия о программировании интеграции со средой CLR](../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
 Объясняет интеграцию компонента среды CLR платформы .NET Framework для [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Это означает, что хранимые процедуры, триггеры, определяемые пользователем типы, функции и агрегатные функции, а также потоковые функции с табличным значением теперь можно разрабатывать с использованием любого языка .NET Framework, включая [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET и [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 [Программирование собственного клиента SQL Server](../relational-databases/native-client/sql-server-native-client-programming.md)  
 Объясняет, как технология [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client может применяться для создания новых или усовершенствования существующих приложений, которым требуется доступ к новым возможностям [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], таким как режим MARS, определяемые пользователем типы, уведомления о запросах, изоляция моментальных снимков и поддержка типа данных XML.  
  
 [Основные понятия о программировании для SQLXML 4.0](../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
 Содержит описание последней версии SQLXML, обеспечивающей те же возможности, что и SQLXML 3.0, а также дополнительные обновления для поддержки новых возможностей [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], например типа данных XML.  
  
 [Основные понятия о поставщике WMI для управления конфигурацией](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
 Описание публикуемого слоя, который используется с оснасткой диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для консоли управления (MMC) и диспетчером конфигурации [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Предоставляет единообразный метод взаимодействия с API-интерфейсом, позволяющий управлять операциями с реестром, запрошенными диспетчером конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], и обеспечивает улучшенное управление выбранным экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 [Основные понятия о поставщике WMI для событий сервера](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
 Приводит описание использования инструментария управления Windows (WMI) для наблюдения за событиями на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 [Руководство по программированию управляющих объектов SQL Server (SMO)](../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
 Содержит сведения об объектах SMO [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], коллекции объектов, разработанных для программирования всех аспектов управления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 [Программирование расширенных хранимых процедур ядра СУБД](../relational-databases/database-engine-extended-stored-procedure-programming.md)  
 Приводит описание использования расширенных хранимых процедур для создания собственных внешних процедур на таком языке программирования, как C.  
  
 [Программирование сборщика данных](http://msdn.microsoft.com/library/53b4752b-055d-4716-b2bc-75b4cce84101)  
 Описывает модель объектов сборщика данных.  
  
 [Программирование окон сообщений об исключениях](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)  
 Объясняет, как использовать программный интерфейс окна сообщений об исключениях, чтобы обеспечить приложениям более полное управление сообщениями и дать пользователям возможность сохранять содержимое сообщения об ошибке для последующего просмотра сообщений и получения помощи при работе с ними.  
  
## <a name="see-also"></a>См. также:  
 [Программирование интеллектуального анализа данных](../analysis-services/data-mining-programming.md)   
 [Документация для разработчика служб Analysis Services](../analysis-services/analysis-services-developer-documentation.md)   
 [Документация для разработчика служб Integration Services](../integration-services/integration-services-developer-documentation.md)   
 [Руководство разработчика по репликации](../relational-databases/replication/concepts/replication-developer-documentation.md)   
 [Документация для разработчика служб Reporting Services](../reporting-services/reporting-services-developer-documentation.md)  
  
  
