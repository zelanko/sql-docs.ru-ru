---
description: Администрирование серверов при помощи среды SQL Server Management Studio
title: Администрирование серверов при помощи среды SQL Server Management Studio
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e22004ab339442cce1e6f09f739ba9f27b867213
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036707"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Администрирование серверов при помощи среды SQL Server Management Studio
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] является полнофункциональным интегрированным административным клиентом, разработанным для решения задач администратора сервера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и Базы данных SQL Azure. В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]задачи администрирования выполняются при помощи обозревателя объектов, который позволяет подключиться к любому серверу семейства [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и просматривать его содержимое при помощи графических средств. Сервер может быть экземпляром компонента [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или базы данных SQL Azure.  
  
В число средств среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] входят зарегистрированные серверы, обозреватель объектов, обозреватель решений, обозреватель шаблонов, страница сводки и окно документа. Чтобы отобразить средство, в меню **Вид** выберите его название. Для отображения редактора запросов нажмите кнопку **Создать запрос** на панели инструментов.  
  
> [!IMPORTANT]  
> По умолчанию сетевой трафик между [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не шифруется. Не работайте в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] с конфиденциальными данными (включая пароли), не установив шифруемого соединения. Дополнительные сведения см. в разделе [Практическое руководство. Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
Используйте среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] для выполнения следующих действий:  
  
-   регистрации серверов;  
  
-   соединения с экземпляром [!INCLUDE[ssDE](../includes/ssde_md.md)], SSAS, [!INCLUDE[ssRS](../includes/ssrs.md)], [!INCLUDE[ssIS](../includes/ssis_md.md)]  или базы данных SQL Azure;  
  
-   настройки свойств сервера;  
  
-   управления объектами базы данных и службами SSAS, такими как кубы, измерения и сборки;  
  
-   создания таких объектов, как базы данных, таблицы, кубы, пользователи базы данных и имена входа;  
  
-   управления файлами и группами файлов;  
  
-   присоединения или отсоединения баз данных;  
  
-   запуска средств для работы со сценариями;  
  
-   управления безопасностью;  
  
-   просмотра системных журналов;  
  
-   контроля текущей активности;  
  
-   настройки репликации;  
  
-   управления полнотекстовыми индексами.  
  
Для запуска и остановки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](./sql-server-management-studio-ssms.md)  
[Практическое руководство. Просмотр свойств сервера (среда SQL Server Management Studio)](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
