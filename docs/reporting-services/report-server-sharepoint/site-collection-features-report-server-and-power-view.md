---
title: "Активация функций интеграции Power View в SharePoint и сервер отчетов | Документы Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: e97378914a59fab938fc3e4c7926847effcffc94
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Активация функций интеграции Power View в SharePoint и сервер отчетов

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  После установки по умолчанию активируются компоненты семейства сайтов службы Reporting Services [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] надстройки для продуктов SharePoint. В некоторых случаях необходимо вручную активировать эти компоненты.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.

 При установке надстройки служб Reporting Services для продуктов SharePoint 2010 после установки продукта SharePoint, затем функцию интеграции сервера отчетов и интеграция Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов необходимо активировать эти компоненты вручную. Например, если у вас есть коллекции сайтов **http://[my имя сервера] /sites/ [имя сайта коллекции]** необходимо вручную активировать компоненты семейства сайтов службы Reporting Services.  
  
 Если нет корневого семейства веб-сайтов, надстройка служб Reporting Services регистрируют сообщение, аналогичное приведенному ниже.  
  
 «Веб-приложение SharePoint 80 не содержит корневого семейства веб-сайтов»  
  
 Чтобы найти сообщение, в журнале установки надстройки с именем «RS_SP_ # .log», где # представляет номер с приращением. Этот файл журнала находится в текущей папке Temp пользователей, например C:\Users\\[имя пользователя] \AppData\Local\Temp. Дополнительные сведения о параметрах ведения журнала надстройки см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>Активировать сервер отчетов и Power View integration возможности коллекции сайтов
  
1.  Откройте в браузере на сайт место функции служб Reporting Services active.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке **Функцию интеграции сервера отчетов** или **Функцию интеграции средства Power View** .  
  
6.  Нажмите кнопку **Активировать**.  
  
 Деактивация компонентов выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>Активация и деактивация службы Reporting Services центра администрирования сайта компонент коллекции
  
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

