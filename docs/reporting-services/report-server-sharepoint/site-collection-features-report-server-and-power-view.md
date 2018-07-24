---
title: Активация функций интеграции с сервером отчетов и Power View в SharePoint | Документы Майкрософт
ms.custom: ''
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c6c6c314ec55a01fb6f2884cd6a5baace396efaf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035232"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Активация функций интеграции с сервером отчетов и Power View в SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Компоненты семейства веб-сайтов служб Reporting Services обычно активируются по умолчанию после установки надстройки служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для продуктов SharePoint. В некоторых ситуациях необходимо активировать эти компоненты вручную.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

 При установке надстройки служб Reporting Services для продуктов SharePoint 2010 после установки SharePoint функции интеграции с сервером отчетов и Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов необходимо активировать эти функции вручную. Например, если имеется семейство веб-сайтов **http://[имя_сервера]/sites/[имя_семейства_веб-сайтов]**, то необходимо вручную активировать функции семейства веб-сайтов служб Reporting Services.  
  
 Когда корневого семейства веб-сайтов нет, надстройка Reporting Services занесет в журнал сообщение, подобное приведенному ниже.  
  
 «Веб-приложение SharePoint 80 не содержит корневого семейства веб-сайтов»  
  
 Сообщение сохраняется в журнале установки надстройки с именем RS_SP_#.log, где # ― это номер с приращением. Файл журнала сохраняется в папку Temp текущего пользователя, например C:\Users\\[имя_пользователя]\AppData\Local\Temp. Дополнительные сведения о параметрах ведения журнала надстройки см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>Активация функций семейства веб-сайтов для интеграции с сервером отчетов и Power View
  
1.  Откройте в браузере сайт, где нужно активировать функции служб Reporting Services.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке **Функцию интеграции сервера отчетов** или **Функцию интеграции средства Power View** .  
  
6.  Нажмите кнопку **Активировать**.  
  
 Деактивация компонентов выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>Активация и деактивация функции семейства веб-сайтов для центра администрирования служб Reporting Services
  
1.  Откройте в браузере центр администрирования SharePoint.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке пункт **Функция центра администрирования сервера отчетов** .  
  
6.  Нажмите кнопку **Активировать**.  
  
 Деактивация компонента выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
## <a name="next-steps"></a>Следующие шаги

После активации компонента можно продолжить интеграцию сервера.

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
