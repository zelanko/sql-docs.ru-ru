---
title: Параметры (SQL Server AlwaysOn, страница панели мониторинга) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Alwayson.Dashboard
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9261f692dfed61174181fce1ff6b9aeb72ab69cc
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936687"
---
# <a name="options-sql-server-alwayson-dashboard-page"></a>Параметры (страница панели мониторинга SQL Server AlwaysOn)
  Для настройки панели мониторинга AlwaysOn используйте страницу **SQL Server AlwaysOn Dashboard** (Панель мониторинга SQL Server) диалогового окна [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**в среде** .  
  
 **Открытие этой страницы**  
  
 В меню **Сервис** щелкните **Параметры**, разверните папку **SQL Server AlwaysOn** и затем выберите **Панель мониторинга**.  
  
## <a name="on-this-page"></a>На этой странице  
 **Включить автоматическое обновление.**  
 Выберите, чтобы включить автоматическое обновление. Доступны следующие параметры.  
  
-   В поле **Интервал обновления (в секундах)** отображается количество секунд, через которое панель будет обновлена. Значение по умолчанию — 30. Если автоматическое обновление включено, значение в этом поле можно изменить, чтобы указать новый интервал обновления.  
  
-   В поле **Количество повторных попыток подключения** отображается, сколько раз панель мониторинга будет пытаться установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором расположена реплика доступности группы доступности, мониторинг которой выполняет панель. Значение по умолчанию — 65535. Если автоматическое обновление включено, значение в этом поле вы можете изменить, чтобы указать другое количество попыток.  
  
 **Включить собственную, определяемую пользователем политику AlwaysOn.**  
 Если вы определили собственную политику AlwaysOn, выберите этот параметр, чтобы включить ее.  
  
## <a name="see-also"></a>См. также:  
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
