---
title: Проверка установки SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34e4c29cb28f76c930f1f04152528ca1a8a89dfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62775237"
---
# <a name="validate-a-sql-server-installation"></a>Проверка установки SQL Server
  С помощью отчета об обнаружении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно проверить, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере. В **отчете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] об обнаруженных компонентах** отображается отчет обо [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]всех [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] продуктах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]и [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]компонентах, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)],,, и, установленных на локальном сервере. Отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступен на странице **Средства** в центре установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчета об обнаружении компонентов:**  
  
 Запустите центр установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для этого в меню **Пуск** выберите **Все программы**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<имя версии>**, **Средства настройки** и **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Центр установки**. Чтобы запустить отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], щелкните **Средства** в левой области навигации **центра установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** и выберите **Установленный отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**.  
  
 Отчет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] об обнаружении сохраняется в% ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<последнем сеансе\>установки.  
  
 Его создание можно запустить из командной строки. Выполните команду "Setup. exe/Action = RunDiscovery" из командной строки. Если добавить в командную строку "/q", то пользовательский интерфейс не будет отображаться, но отчет по-прежнему будет создан в% ProgramFiles\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]% \120\Setup\\ Bootstrap\Log<последнем сеансе\>установки.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
