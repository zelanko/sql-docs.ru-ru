---
title: Параметры (страница «результаты запроса и службы зависимостей») | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d19228fdf17788e9118367a6f0f0eb3be90cb72a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930136"
---
# <a name="options-query-results-and-dependency-services-page"></a>Параметры ("Результаты запроса" и страница "Службы зависимостей")
  Используйте эту страницу, чтобы указать сервер для подключения к службам зависимостей. Службы зависимостей позволяют извлекать данные о зависимостях между объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], сохраненными на разных серверах. Просмотреть зависимости объектов можно с помощью диалогового окна « **зависимости объектов** » в среде [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] .  
  
 **Выберите действие**  
  
1.  [Откройте диалоговое окно «Параметры» (страницу результатов запроса или служб зависимостей)](#open_dialog)  
  
2.  [Настройка параметров](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>Открытие диалогового окна «Параметры» (страница «результаты запроса/службы зависимостей»)  
  
1.  В выберите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] пункт **Параметры** в меню **Сервис** .  
  
2.  Разверните **Результаты запроса** и нажмите кнопку **Службы зависимостей**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Настройка параметров  
  
### <a name="options"></a>Варианты  
 **Сервер служб зависимостей**  
 Укажите сервер, на котором установлены службы зависимостей.  
  
 **Аутентификация**  
 Выберите проверку подлинности Windows, чтобы войти в систему с использованием учетной записи Microsoft Windows, или выберите проверку подлинности SQL Server.  
  
 При подключении пользователя с указанным именем и паролем через недоверенное соединение, SQL Server выполняет проверку подлинности посредством проверки настройки учетной записи входа SQL Server и совпадения указанного пароля с предварительно сохраненными. Если SQL Server не может найти такое имя входа, проверка подлинности прекращается и пользователь получает сообщение об ошибке.  
  
 **User name**  
 При использовании проверки подлинности SQL Server укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности SQL Server укажите пароль.  
  
 **Тест**  
 Щелкните, чтобы проверить соединение.