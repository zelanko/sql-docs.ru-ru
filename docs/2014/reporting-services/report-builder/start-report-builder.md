---
title: Запуск построителя отчетов (построитель отчетов) | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 50
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: bb09858869f76fd32a1e05151eef48870f96f68a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192841"
---
# <a name="start-report-builder-report-builder"></a>Запуск построителя отчетов (построитель отчетов)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] включает в себя автономного и [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] версий построителя отчетов. Версию [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] можно использовать со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], установленными в собственном режиме или в режиме интеграции с SharePoint.  
  
> [!NOTE]  
>  Построитель отчетов нельзя устанавливать на компьютеры с процессорами Itanium 64. Это относится к [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] и к изолированной версии построителя отчетов.  
  
 Если открывается версия [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] для построителя отчетов предыдущей версии, обратитесь к администратору, который может обновить диспетчер отчетов и сайт SharePoint для использования версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] построителя отчетов.  
  
 Версию [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] построителя отчетов можно также использовать для создания отчетов по книге [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], опубликованной в SharePoint. Дополнительные сведения об использовании построителя отчетов с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], в разделе [создания отчетов служб Reporting Services с данными PowerPivot](http://go.microsoft.com/fwlink/?LinkId=185238) на сайте technet.microsoft.com.  
  
 Запуск построителя отчетов из автономного **запустить** меню на локальном компьютере, пользователь или администратор необходимо установить построитель отчетов непосредственно на компьютере, прежде чем программа доступна для использования. Изолированная версия не устанавливается вместе с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Ее необходимо загрузить и установить отдельно. Загрузить построитель отчетов [построитель отчетов Microsoft® SQL Server® 2012](http://go.microsoft.com/fwlink/?LinkId=401502).  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>Запуск версии ClickOnce построителя отчетов из диспетчера отчетов  
  
1.  В веб-браузере введите в адресной строке URL-адрес для сервера отчетов. URL-адрес по умолчанию — http://\<*имя_сервера*>/reports. Откроется диспетчер отчетов.  
  
2.  Щелкните **Построитель отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>Запуск построителя отчетов ClickOnce с помощью URL-адреса  
  
1.  В адресной строке веб-браузера введите следующий URL-адрес:  
  
     http://\<имя_сервера > /reportserver/reportbuilder/ReportBuilder_3_0_0_0.application  
  
2.  Нажмите клавишу ВВОД.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>Запуск построителя отчетов ClickOnce в режиме интеграции с SharePoint  
  
1.  Перейдите на сайт SharePoint, содержащий нужную библиотеку.  
  
2.  Откройте библиотеку.  
  
3.  Нажмите **Документы**.  
  
4.  В меню **Создать документ** выберите пункт **Отчет построителя отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
     **Примечание** Если **новый документ** не отображаются в меню **отчет в построителе отчетов**, **модель построителя отчетов**, и **источник данных отчета** параметры, типы их содержимого должны быть добавлены в библиотеку SharePoint. Дополнительные сведения см. в разделе [Добавление типов сервера отчетов содержимого в библиотеку &#40;служб Reporting Services в режиме интеграции с SharePoint&#41; ](../add-reporting-services-content-types-to-a-sharepoint-library.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [электронной документации по](http://go.microsoft.com/fwlink/?LinkId=154888) на MSDN.Microsoft.com.  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>Запуск изолированной версии построителя отчетов из меню «Пуск»  
  
1.  В меню «Пуск» выберите **все программы**, а затем нажмите кнопку [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **построитель**.  
  
2.  Щелкните **Построитель отчетов** .  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет.  
  
3.  Чтобы создать отчет, щелкните значок SQL Server в верхнем левом углу построителя отчетов, а затем нажмите кнопку «Создать».  
  
4.  Чтобы открыть существующий отчет, сохраненный на локальном компьютере или сервере отчетов, щелкните значок SQL Server в верхнем левом углу построителя отчетов, а затем нажмите кнопку «Открыть».  
  
     Если вы не видите сервера отчетов в списке существующих серверов, закройте **открыть отчет** диалоговое окно и нажмите кнопку **Connect** в нижней части построителя отчетов для подключения к серверу.  
  
## <a name="see-also"></a>См. также  
 [Построитель отчетов в SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  