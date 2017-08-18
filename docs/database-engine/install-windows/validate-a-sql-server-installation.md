---
title: "Проверка установки SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 341c3b515d346ee42c8f5e9b01a78b9f3ca08569
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="validate-a-sql-server-installation"></a>Проверка установки SQL Server
  С помощью отчета об обнаружении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно проверить, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере. На странице **Отчет об обнаруженных установленных компонентах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** отображается отчет обо всех продуктах и компонентах [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], установленных на локальном сервере. Отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступен на странице **Средства** в центре установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Запуск отчета об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Запустите центр установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для этого в меню **Пуск** выберите **Все программы**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<имя версии>**, **Средства настройки** и **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Центр установки**. Чтобы запустить отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], щелкните **Средства** в левой области навигации **центра установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** и выберите **Установленный отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**.  
  
 Отчет об обнаружении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняется в папке %ProgramFiles%\\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<последний сеанс программы установки\>.  
  
 Его создание можно запустить из командной строки. Выполните команду "Setup.exe /Action=RunDiscovery". Если в командную строку добавить "/q", то пользовательский интерфейс не отображается, но отчет будет создан в каталоге %ProgramFiles%\\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]130\Setup Bootstrap\Log\\<последний сеанс программы установки\>.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
