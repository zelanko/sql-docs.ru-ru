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
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931705"
---
# <a name="validate-a-sql-server-installation"></a>Проверка установки SQL Server
  С помощью отчета об обнаружении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно проверить, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и какие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены на компьютере. В ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчете об обнаруженных компонентах** отображается отчет обо всех [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] продуктах и компонентах,,,, и, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] установленных на локальном сервере. Отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступен на странице **Средства** в центре установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчета об обнаружении компонентов:**  
  
 Запустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] центр установки, в меню **Пуск** последовательно укажите пункты **все программы**, ** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name> **, **средства настройки**и выберите ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] центр установки**. Чтобы запустить отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], щелкните **Средства** в левой области навигации **центра установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** и выберите **Установленный отчет об обнаружении компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Отчет об обнаружении сохраняется в% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<последнем сеансе установки \> .  
  
 Его создание можно запустить из командной строки. Выполните команду "Setup.exe/Action = RunDiscovery" из командной строки. Если добавить в командную строку "/q", то пользовательский интерфейс не будет отображаться, но отчет по-прежнему будет создан в% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<последнем сеансе установки \> .  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
