---
title: Неподдерживаемые возможности средств управления в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 6e58acd0-73c5-4161-9fbc-8ea531bc681c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c966c3e4388588810438d7e91a9ae0356ef60c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780353"
---
# <a name="discontinued-management-tools-features-in-sql-server-2014"></a>Неподдерживаемые возможности средств управления в SQL Server 2014
  В этом разделе описываются функции средств управления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , которые недоступны в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="features-removed-in-includesscurrentincludessscurrent-mdmd"></a>Функции, удаленные в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 None  
  
## <a name="features-removed-in-includesssql11includessssql11-mdmd"></a>Функции, удаленные в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="sql-server-compact-edition"></a>SQL Server Compact Edition  
 Редактор кода SQL Server Compact Edition исключен из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Поддержка SQL Server Compact Edition также исключена из обозревателя объектов, обозревателя решений и обозревателя шаблонов. Вместо них используйте редакторы Transact-SQL в среде Microsoft Visual Studio 2010 с пакетом обновления 1 (SP1) или в WebMatrix.  
  
### <a name="activex-subsystem-for-sql-server-agent"></a>Подсистема ActiveX для агента SQL Server  
 В этом выпуске была удалена подсистема ActiveX для агента SQL Server. Заменяющая ее функциональность отсутствует.  
  
### <a name="spaddtask-spdeletetask-spupdatetask"></a>sp_addtask, sp_deletetask, sp_updatetask  
 В этом выпуске были удалены хранимые процедуры sp_addtask, sp_deletetask и sp_updatetask. Не следует использовать эту функциональность в новых и обновляемых приложениях.  
  
### <a name="net-send-and-pager-notification"></a>NET SEND и уведомления на пейджер  
 В этом выпуске были удалены отправка сообщений с помощью NET SEND и уведомлений на пейджер. Не следует использовать эту функциональность в новых и обновляемых приложениях.  
  
### <a name="data-tier-applications"></a>Приложения уровня данных  
 Некоторые компоненты приложения уровня данных (DAC), присутствующие в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] , были удалены из [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Тем не менее, платформа приложения уровня данных (DACFx, версия 3.0), выпущенная вместе с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], совместима с [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] — [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]. Версия DAC 3.0 не поддерживается более ранними версиями [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , включая [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]. Проекты базы данных Visual Studio 2010 не поддерживают пакеты приложения уровня данных 3.0 (DACPAC) или пакеты экспорта приложения уровня данных (BACPAC), созданные в DACFx 3.0 или более поздней версии.  
  
 Рекомендуется использовать последнюю версию проекта базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools.  
  
 API DACFx 3.0 и средства [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживают чтение DACPAC- и BACPAC-файлов, созданных с помощью более ранних версий средств [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и DACFx: извлечение баз данных из этих версий в DACPAC-файлы и развертывание в поддерживаемые версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] или [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools.  
  
## <a name="see-also"></a>См. также  
 [Обратная совместимость](../../2014/getting-started/backward-compatibility.md)  
  
  
