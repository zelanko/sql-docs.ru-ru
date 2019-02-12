---
title: Активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 69d059807b7d48fe71cffb120c73fa9aa004a8bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018006"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint
  Функция синхронизации файлов сервера отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] использует обработчики событий SharePoint для синхронизации каталога сервера отчетов с элементами в библиотеках документов. Эта функция может оказаться полезной в том случае, если пользователи часто передают элементы опубликованных отчетов напрямую в библиотеки документов SharePoint. Если функция синхронизации файлов не включена, содержимое будет синхронизироваться, но не так часто.  
  
 Функция синхронизации файлов активируется в центре администрирования сайта SharePoint после установки надстройки служб [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] для продуктов SharePoint.  
  
 Эту функцию можно активировать и деактивировать вручную не на уровне семейства веб-сайтов, а раздельно для каждого сайта.  
  
## <a name="prerequisites"></a>предварительные требования  
 Надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для SharePoint должна быть установлена. Если надстройка не установлена, функция синхронизации файлов не будет отображаться в списке функций сайта.  
  
 Чтобы проверить установку, просмотрите список установленных приложений на [!INCLUDE[msCoName](../includes/msconame-md.md)] **панели управления** Windows. Если надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] установлена, следуйте инструкциям в этом разделе для активации функции синхронизации файлов сервера отчетов.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Активация и деактивация функции синхронизации файлов служб Reporting Services на сайте  
  
1.  На главной странице сайта откройте меню **Действия сайта** и выберите пункт **Настройки веб-сайта**.  
  
2.  В меню **Действия сайта** выберите пункт **Управление функциями сайта**.  
  
3.  Найдите в списке **Синхронизация файлов сервера отчетов** .  
  
4.  Нажмите кнопку **Активировать**.  
  
> [!NOTE]  
>  Деактивировать функцию синхронизации файлов сервера отчетов можно с помощью той же процедуры, но выбрав пункт **Деактивировать**.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок в элементах отчета &#40;построитель отчетов и службы SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
