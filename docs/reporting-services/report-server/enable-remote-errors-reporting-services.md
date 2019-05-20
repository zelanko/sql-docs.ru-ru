---
title: Включение отслеживания удаленных ошибок (службы Reporting Services) | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 045689c0aa7f5b4bbc8a365ad2d15d77f3b67ce4
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65577759"
---
# <a name="enable-remote-errors-reporting-services"></a>Включение отслеживания удаленных ошибок (службы Reporting Services)
  Можно задать свойства сервера на сервере отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , чтобы возвращались дополнительные сведения об ошибках, возникающих на удаленных серверах. Если сообщение об ошибке содержит текст «Чтобы получить дополнительные сведения об этой ошибке, перейдите к серверу отчетов на локальном сервере или включите отслеживание удаленных ошибок», то можно задать свойство **EnableRemoteErrors** , чтобы получить доступ к дополнительным сведениям, которые могут помочь в устранении возникшей неполадки. Дополнительные сведения см. в разделе [Системные свойства сервера отчетов](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 В этом разделе:  
  
-   [Включение отслеживания удаленных ошибок для режима SharePoint](#bkmk_sharepoint)  
  
-   [Включение отслеживания удаленных ошибок в среде SQL Server Management Studio (собственный режим)](#bkmk_mgtStudio)  
  
-   [Включение отслеживания удаленных ошибок с помощью скрипта (собственный режим)](#bkmk_script)  
  
-   [Изменение таблицы ConfigurationInfo (собственный режим)](#bkmk_ConfigurationInfo)  
  
##  <a name="bkmk_sharepoint"></a> Включение отслеживания удаленных ошибок для режима SharePoint  
 Существуют две различные процедуры для включения отслеживания удаленных ошибок для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме совместимости с SharePoint. Процедуры для двух разных архитектур сервера отчетов отличаются. В выпуске [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] была представлена новая архитектура, основанная на службах SharePoint. В ней используются настройки, которые могут быть изменены для каждого приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Прежняя архитектура использовала общие настройки на уровне веб-сайта.  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a>Включение отслеживания удаленных ошибок для приложения службы Reporting Services  
  
1.  Для сервера отчетов в режиме интеграции с SharePoint, установленном с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или обновленной версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], включите настройку приложения службы **Включение удаленного контроля ошибок**. Настройка может быть изменена для каждого приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  В центре администрирования SharePoint в разделе **Управление приложениями** выберите **Управление приложениями служб** .  
  
3.  Найдите нужное приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и щелкните его название.  
  
4.  Нажмите кнопку **Системные параметры**.  
  
5.  В разделе **Безопасность** нажмите кнопку **Включить отслеживание удаленных ошибок** .  
  
6.  Нажмите кнопку **ОК**.  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a>Включение отслеживания удаленных ошибок для сайта SharePoint  
  
1.  Для сервера отчетов в режиме интеграции с SharePoint, установленном с версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], включите настройку сайта **Включение удаленного контроля ошибок в локальном режиме**.  
  
2.  В области **Действия сайта** выберите **Настройки сайта** для сайта, который необходимо изменить.  
  
3.  Выберите **Настройки сайта служб Reporting Services** в группе **Reporting Services** .  
  
4.  Выберите **Включить отслеживание удаленных ошибок в локальном режиме**.  
  
5.  Нажмите кнопку **ОК**.  
  
##  <a name="bkmk_mgtStudio"></a> Включение отслеживания удаленных ошибок в среде SQL Server Management Studio (собственный режим)  
  
1.  Запустите среду Management Studio и соединитесь с экземпляром сервера отчетов. Дополнительные сведения см. в разделе [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Щелкните правой кнопкой мыши узел сервера отчетов и выберите пункт **Свойства**.  
  
3.  Нажмите кнопку **Дополнительно** , чтобы открыть страницу свойств. Дополнительные сведения см. в разделе [Свойства сервера (страница "Дополнительно") — службы Reporting Services](../../reporting-services/tools/server-properties-advanced-page-reporting-services.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  В поле **EnableRemoteErrors**выберите значение **True**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="bkmk_script"></a> Включение отслеживания удаленных ошибок с помощью скрипта (собственный режим)  
  
1.  Создайте текстовый файл и скопируйте в него следующий скрипт.  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  Сохраните файл с именем EnableRemoteErrors.rss.  
  
3.  Нажмите кнопку **Пуск**, укажите команду **Выполнить**, введите **cmd**и нажмите кнопку **ОК** , чтобы открыть окно командной строки.  
  
4.  Перейдите к каталогу, содержащему только что созданный файл RSS.  
  
5.  Введите в командной строке следующую команду, заменив местозаполнитель *имя_сервера* реальным именем сервера:  
  
    ```  
    rs -i EnableRemoteErrors.rss -s https://servername/ReportServer  
    ```  
  
6.  Дополнительные сведения см. в разделе [Программа RS.exe (SSRS)](../../reporting-services/tools/rs-exe-utility-ssrs.md).  
  
##  <a name="bkmk_ConfigurationInfo"></a> Изменение таблицы ConfigurationInfo (собственный режим)  
  
> [!NOTE]  
>  Столбцу **True** в таблице **ConfigurationInfo** в базе данных сервера отчетов можно присвоить значение **EnableRemoteErrors**, но если сервер отчетов активно используется, то изменение этих настроек необходимо производить в среде SQL Server Management Studio или с помощью скрипта. При изменении настроек базы данных необходимо перезапустить службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , чтобы изменения вступили в силу.  
  
  
