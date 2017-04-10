---
title: "активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint
  Функция синхронизации файлов сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использует обработчики событий SharePoint для синхронизации каталога сервера отчетов с элементами в библиотеках документов. Эта функция может оказаться полезной в том случае, если пользователи часто передают элементы опубликованных отчетов напрямую в библиотеки документов SharePoint. Если функция синхронизации файлов не включена, содержимое будет синхронизироваться, но не так часто.  
  
 Функция синхронизации файлов активируется в центре администрирования сайта SharePoint после установки надстройки служб [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для продуктов SharePoint.  
  
 Эту функцию можно активировать и деактивировать вручную не на уровне семейства веб-сайтов, а раздельно для каждого сайта.  
  
## Предварительные требования  
 Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint должна быть установлена. Если надстройка не установлена, функция синхронизации файлов не будет отображаться в списке функций сайта.  
  
 Чтобы проверить установку, просмотрите список установленных приложений на [!INCLUDE[msCoName](../../includes/msconame-md.md)] панели управления ** **Windows. Если надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установлена, следуйте инструкциям в этом разделе для активации функции синхронизации файлов сервера отчетов.  
  
### Активация и деактивация функции синхронизации файлов служб Reporting Services на сайте  
  
1.  На главной странице сайта откройте меню **Действия сайта** и выберите пункт **Настройки веб-сайта**.  
  
2.  В меню **Действия сайта** выберите пункт **Управление функциями сайта**.  
  
3.  Найдите в списке **Синхронизация файлов сервера отчетов** .  
  
4.  Нажмите кнопку **Активировать**.  
  
> [!NOTE]  
>  Деактивировать функцию синхронизации файлов сервера отчетов можно с помощью той же процедуры, но выбрав пункт **Деактивировать**.  
  
## См. также  
 [Устранение неполадок в элементах отчета (построитель отчетов и службы SSRS)](http://msdn.microsoft.com/ru-ru/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Установка и удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Установка и удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  