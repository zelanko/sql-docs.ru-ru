---
title: Запуск построитель отчетов (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6fc123be862320cd35ccf4aec76d8bc9cf7877af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107603"
---
# <a name="start-report-builder-report-builder"></a>Запуск построителя отчетов (построитель отчетов)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]включает изолированные версии и [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] построитель отчетов. Версию [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] можно использовать со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], установленными в собственном режиме или в режиме интеграции с SharePoint.  
  
> [!NOTE]  
>  Построитель отчетов нельзя устанавливать на компьютеры с процессорами Itanium 64. Это относится и к версии [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] , и к изолированной версии построителя отчетов.  
  
 Если открывается версия [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] для построителя отчетов предыдущей версии, обратитесь к администратору, который может обновить диспетчер отчетов и сайт SharePoint для использования версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] построителя отчетов.  
  
 Версию [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] построителя отчетов можно также использовать для создания отчетов по книге [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], опубликованной в SharePoint. Дополнительные сведения об использовании построитель отчетов с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]см. в разделе [Создание Reporting Services отчета с данными PowerPivot](https://go.microsoft.com/fwlink/?LinkId=185238) в TechNet.Microsoft.com.  
  
 Чтобы начать построитель отчетов автономно из меню " **Пуск** " на локальном компьютере, вам или администратору необходимо установить построитель отчетов непосредственно на компьютере, прежде чем средство будет доступно для использования. Изолированная версия не устанавливается вместе с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Ее необходимо загрузить и установить отдельно. Сведения о загрузке построитель отчетов см. в разделе [Microsoft® SQL Server® 2012 построитель отчетов](https://go.microsoft.com/fwlink/?LinkId=401502).  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>Запуск версии ClickOnce построителя отчетов из диспетчера отчетов  
  
1.  В веб-браузере введите в адресной строке URL-адрес для сервера отчетов. URL-адрес по умолчанию —\<http://*ServerName*>/Reports. Откроется диспетчер отчетов.  
  
2.  Щелкните **Построитель отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>Запуск построителя отчетов ClickOnce с помощью URL-адреса  
  
1.  В адресной строке веб-браузера введите следующий URL-адрес:  
  
     http://\<ServerName>/репортсервер/репортбуилдер/ReportBuilder_3_0_0_0. Application  
  
2.  Нажмите клавишу ВВОД.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>Запуск построителя отчетов ClickOnce в режиме интеграции с SharePoint  
  
1.  Перейдите на сайт SharePoint, содержащий нужную библиотеку.  
  
2.  Откройте библиотеку.  
  
3.  Нажмите **Документы**.  
  
4.  В меню **Создать документ** выберите пункт **Отчет построителя отчетов**.  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
     **Примечание** . Если в меню " **создать документ** " не перечислены **построитель отчетов отчет**, **Построитель отчетов модель**и параметры **источника данных отчета** , их типы содержимого необходимо добавить в библиотеку SharePoint. Дополнительные сведения см. в разделе [Добавление типов содержимого сервера отчетов в библиотеку &#40;Reporting Services в режиме интеграции с SharePoint&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [электронной документации](https://go.microsoft.com/fwlink/?LinkId=154888) по MSDN.Microsoft.com.  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>Запуск изолированной версии построителя отчетов из меню «Пуск»  
  
1.  В меню Пуск выберите пункт **все программы**, а затем щелкните [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **Построитель отчетов**.  
  
2.  Щелкните **Построитель отчетов** .  
  
     Откроется построитель отчетов, и можно будет приступить к созданию отчета или открыть отчет.  
  
3.  Чтобы создать отчет, щелкните значок SQL Server в верхнем левом углу построителя отчетов, а затем нажмите кнопку «Создать».  
  
4.  Чтобы открыть существующий отчет, сохраненный на локальном компьютере или сервере отчетов, щелкните значок SQL Server в верхнем левом углу построителя отчетов, а затем нажмите кнопку «Открыть».  
  
     Если сервер отчетов не отображается в списке существующих серверов, закройте диалоговое окно **Открытие отчета** и нажмите кнопку **Подключиться** в нижней части построитель отчетов, чтобы подключиться к серверу.  
  
## <a name="see-also"></a>См. также:  
 [Построитель отчетов в SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
