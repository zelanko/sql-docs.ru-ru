---
title: Параметры (результаты запроса и страница "службы зависимостей") | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3c5c7afe44889dd380e9048044a34a94410213f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774938"
---
# <a name="options-query-results-and-dependency-services-page"></a>Параметры ("Результаты запроса" и страница "Службы зависимостей")
  Используйте эту страницу, чтобы указать сервер для подключения к службам зависимостей. Службы зависимостей позволяют извлекать данные о зависимостях между объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], сохраненными на разных серверах. Просмотр зависимостей объектов с помощью **зависимости объектов** диалогового окна в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Выбор действия**  
  
1.  [Откройте диалоговое окно параметров (страница "службы запроса результаты/зависимостей")](#open_dialog)  
  
2.  [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a> Откройте диалоговое окно параметров (страница "службы запроса результаты/зависимостей")  
  
1.  В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], нажмите кнопку **параметры** на **средства** меню.  
  
2.  Разверните **Результаты запроса** и нажмите кнопку **Службы зависимостей**.  
  
##  <a name="options"></a> Настройка параметров  
  
### <a name="options"></a>Параметры  
 **Сервер служб зависимостей**  
 Укажите сервер, на котором установлены службы зависимостей.  
  
 **Authentication**  
 Выберите проверку подлинности Windows, чтобы войти в систему с использованием учетной записи Microsoft Windows, или выберите проверку подлинности SQL Server.  
  
 При подключении пользователя с указанным именем и паролем через недоверенное соединение, SQL Server выполняет проверку подлинности посредством проверки настройки учетной записи входа SQL Server и совпадения указанного пароля с предварительно сохраненными. Если SQL Server не может найти такое имя входа, проверка подлинности прекращается и пользователь получает сообщение об ошибке.  
  
 **Имя пользователя**  
 При использовании проверки подлинности SQL Server укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности SQL Server укажите пароль.  
  
 **Тест**  
 Щелкните, чтобы проверить соединение.