---
title: Параметры (страница SQL Server AlwaysOn, панели мониторинга) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Alwayson.Dashboard
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 553f76520f9bb292d795fbbd5e13833391d6bdab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180336"
---
# <a name="options-sql-server-alwayson-dashboard-page"></a>Параметры (страница панели мониторинга SQL Server AlwaysOn)
  Для настройки панели мониторинга AlwaysOn используйте страницу **SQL Server AlwaysOn Dashboard** (Панель мониторинга SQL Server) диалогового окна [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**в среде** .  
  
 **Открытие этой страницы**  
  
 В меню **Сервис** щелкните **Параметры**, разверните папку **SQL Server AlwaysOn** и затем выберите **Панель мониторинга**.  
  
## <a name="on-this-page"></a>На этой странице  
 **Включить автоматическое обновление.**  
 Выберите, чтобы включить автоматическое обновление. Доступны следующие возможности:  
  
-   В поле **Интервал обновления (в секундах)** отображается количество секунд, через которое панель будет обновлена. Значение по умолчанию — 30. Если автоматическое обновление включено, значение в этом поле можно изменить, чтобы указать новый интервал обновления.  
  
-   В поле **Количество повторных попыток подключения** отображается, сколько раз панель мониторинга будет пытаться установить соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором расположена реплика доступности группы доступности, мониторинг которой выполняет панель. Значение по умолчанию — 65535. Если автоматическое обновление включено, значение в этом поле вы можете изменить, чтобы указать другое количество попыток.  
  
 **Включите собственную политику AlwaysOn определяемой пользователем.**  
 Если вы определили собственную политику AlwaysOn, выберите этот параметр, чтобы включить ее.  
  
## <a name="see-also"></a>См. также  
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  