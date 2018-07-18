---
title: Проверка установки SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ba9a0603e97de67c9bb7ad94acffe4a666d1339
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291380"
---
# <a name="validate-a-sql-server-installation"></a>Проверка установки SQL Server
  С помощью отчета об обнаружении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно проверить, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере. **Установленные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчет об обнаружении компонентов** отображается отчет обо всех [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] продуктов и функций, будут установлены на локальном сервере. Отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступен на странице **Средства** в центре установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Запуск отчета об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Запустите центр установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для этого в меню **Пуск** выберите **Все программы**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<имя версии>**, **Средства настройки** и **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Центр установки**. Чтобы запустить отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], щелкните **Средства** в левой области навигации **центра установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** и выберите **Установленный отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Отчет об обнаружении сохраняется в папке % ProgramFiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< последний сеанс программы установки\>.  
  
 Его создание можно запустить из командной строки. Запустите «Setup.exe/Action = RunDiscovery» из командной строки, если добавить «/ q» в командную строку выше пользовательский Интерфейс не отображается, но отчет будет создан в папке % ProgramFiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< последний сеанс программы установки\>.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и чтение файлов журналов программы установки SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
