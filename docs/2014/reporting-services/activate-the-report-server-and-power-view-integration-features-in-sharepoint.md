---
title: Активация функций интеграции сервера отчетов и Power View в SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30ae6ea0e7fa314748c4da265650273c0a7d56e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110027"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint
  Компоненты [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] семейства веб-сайтов обычно активируются по умолчанию после установки [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] надстройки для продуктов SharePoint. В некоторых ситуациях эти функции требуется активировать вручную.  
  
 При установке надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint 2010 после установки продукта SharePoint функции интеграции с сервером отчетов и с Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов потребуется активировать эти функции вручную. Например, если имеется семейство веб-сайтов **http://[имя_сервера]/sites/[имя_семейства_веб-сайтов]** , то потребуется вручную активировать функции семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 Когда корневого семейства веб-сайтов нет, надстройка [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] занесет в журнал сообщение, подобное приведенному далее.  
  
 «Веб-приложение SharePoint 80 не содержит корневого семейства веб-сайтов»  
  
 Сообщение будет найдено в журнале установки надстройки с именем "RS_SP_ #. log", где # — это увеличивающийся номер. Файл журнала будет находиться в папке Temp текущего пользователя, например C:\Users\\[имя пользователя] \AppData\Local\Temp. Дополнительные сведения о параметрах ведения журнала в надстройке см. в разделе [Установка или удаление надстройки Reporting Services для sharepoint &#40;sharepoint 2010 и sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 В этом разделе:  
  
-   [Активация функций семейства веб-сайтов для интеграции с сервером отчетов и Power View](#bkmk_features)  
  
-   [Активация и деактивация функций семейства веб-сайтов для центра администрирования служб Reporting Services](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a>Чтобы активировать компоненты семейства веб-сайтов интеграции с сервером отчетов и Power View:  
  
1.  Откройте в браузере веб-сайт, где нужно активировать функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке **Функцию интеграции сервера отчетов** или **Функцию интеграции средства Power View** .  
  
6.  Щелкните **Активировать**.  
  
 Деактивация компонентов выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a>Для активации или деактивации Reporting Services компонента семейства веб-сайтов центра администрирования:  
  
1.  Откройте в браузере центр администрирования SharePoint.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке пункт **Функция центра администрирования сервера отчетов** .  
  
6.  Щелкните **Активировать**.  
  
 Деактивация компонента выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 После активации компонента можно продолжить интеграцию сервера.  
  
## <a name="see-also"></a>См. также  
 [Установка или удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
