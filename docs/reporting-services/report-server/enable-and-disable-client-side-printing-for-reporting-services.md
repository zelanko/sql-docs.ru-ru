---
title: Включение и отключение печати на стороне клиента для служб Reporting Services | Документы Майкрософт
description: Сведения о том, как включить или отключить печать на стороне клиента для отчетов Reporting Services, просматриваемых в браузере. Печать на стороне клиента использует формат PDF и включена по умолчанию.
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- pdf
- viewer
- reportviewer
- toolbar
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4a2f61a8700c24a2cc41192103f57a51befbbd15
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390661"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Включение и отключение печати на стороне клиента для служб Reporting Services

  Кнопка печати на панели инструментов средства просмотра отчетов позволяет использовать формат PDF для печати отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , просматриваемых в браузере, на стороне клиента. В новой функции удаленной печати для преобразования отчета в формат PDF используется модуль подготовки отчетов, который входит в состав [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Вы можете скачать отчет в формате PDF. А если у вас есть установленное приложение для просмотра PDF-файлов, с помощью кнопки печати можно отобразить диалоговое окно со стандартными средствами для настройки параметров страницы, включая ее размер и ориентацию, а также возможность предварительного просмотра PDF-файла. Хотя по умолчанию клиентская печать допускается, эту функцию можно отключить.  
  
 В предыдущих версиях [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использовался элемент управления ActiveX, который приходилось скачивать с сервера отчетов на клиентский компьютер. Если вы обновите сервер отчетов до версии SQL Server 2016 или более поздней, элемент управления печатью не будет автоматически удален с сервера отчетов или клиентских компьютеров.  

##  <a name="the-print-experience"></a><a name="bkmk_clientside_printexpereince"></a> Процесс печати  
 Когда вы нажимаете кнопку печати ![htmlviewer_print](../../reporting-services/report-server/media/htmlviewer-print.png "htmlviewer_print") на панели инструментов средства просмотра отчетов, могут открываться разные интерфейсы в зависимости от используемого браузера и установленных на клиентском компьютере приложений для просмотра PDF-файлов.   Учитывая конфигурацию клиентского компьютера, вы сможете скачать PDF-файл, настроить в диалоговом окне параметры печати или выбрать оба варианта.  
  
 ![Панель инструментов «Отчеты»](../../reporting-services/media/ssrs-htmlviewer-toolbar.png "Панель инструментов «Отчеты»")  
  
|Взаимодействие|Пользовательский интерфейс|  
|-|-|  
|Первое диалоговое окно будет одинаковым во всех браузерах. Здесь вы можете изменить базовые параметры печати, например ориентацию страницы. Когда вы нажмете кнопку **Печать**, дальнейший процесс в разных браузерах будет немного отличаться.|![ssrs_pdfprint_chrome1](../../reporting-services/report-server/media/ssrs-pdfprint-chrome1.png "ssrs_pdfprint_chrome1")|  
|В браузере Chrome откроется диалоговое окно печати с подробными настройками.   Здесь можно изменить параметры печати, распечатать файл или открыть стандартное для операционной системы диалоговое окно печати.|![ssrs_pdfprint_chrome2](../../reporting-services/report-server/media/ssrs-pdfprint-chrome2.png "ssrs_pdfprint_chrome2") ![ssrs_pdfprint_chrome3.png](../../reporting-services/report-server/media/ssrs-pdfprint-chrome3-png.png "ssrs_pdfprint_chrome3.png")|  
|Если у вас установлено приложение для просмотра PDF-файлов, кнопка печати откроет окно предварительного просмотра PDF-файла, где этот файл можно сохранить или распечатать.||  
|Если такое приложение у вас не установлено, есть два варианта:<br /><br /> Отчет будет автоматически преобразован для просмотра и обработан браузером для скачивания PDF-файла.   **Примечание.** Чем сложнее отчет, тем больше будет задержка между нажатием кнопки **Печать** и появлением уведомления браузера о скачивании файла. Вы можете принудительно запустить повторное скачивание, перейдя по ссылке **Щелкните здесь для просмотра отчета в формате PDF**.<br /><br /> Для принудительного скачивания PDF-файла перейдите по ссылке **Щелкните здесь для просмотра отчета в формате PDF**.|![ssrs_pdfprint_firefox2](../../reporting-services/report-server/media/ssrs-pdfprint-firefox2.png "ssrs_pdfprint_firefox2")|  
  
##  <a name="troubleshoot-client-side-printing"></a><a name="bkmk_troubleshoot_clientsideprinting"></a> Устранение неполадок печати на стороне клиента  
 Если кнопка печати на панели инструментов средства просмотра отчетов отключена, проверьте следующее.  
  
-   Функция печати на стороне клиента для сервера отчетов отключена в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. См. подраздел  [Включение и отключение печати на стороне клиента](#bkmk_enable) в этом разделе.  
  
-   Отключен модуль подготовки отчетов в формате PDF в [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] . Изучите раздел `<Extension Name="PDF"` в файле **rsreportserver.config** .  
  
-   Вы просматриваете отчет в режиме сравнения, в котором используется устаревший механизм визуализации [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] HTML4. Для печати в формате PDF требуется механизм визуализации HTML5.  Нажмите кнопку **Предварительный просмотр** на панели инструментов.  
  
     ![ssrs_html5_switch2html5](../../reporting-services/report-server/media/ssrs-html5-switch2html5.png "ssrs_html5_switch2html5")  
  
##  <a name="enable-and-disable-client-side-printing"></a><a name="bkmk_enable"></a> Включение и отключение печати на стороне клиента  
 Администраторы сервера отчетов могут отключать функцию удаленной печати. Для этого нужно установить значение **false** для системного свойства **EnableClientPrinting**сервера отчетов. Это отключает клиентскую печать всех отчетов, управляемых этим сервером. По умолчанию **EnableClientPrinting** установлено как **true**. Вы можете запретить печать на стороне клиента следующими способами.  
  
-   Для **сервера отчетов в собственном режиме**  
  
    1.  Запустите [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] с правами администратора.  
  
    2.  Подключитесь к экземпляру сервера отчетов в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    3.  Щелкните правой кнопкой мыши узел сервера отчетов и выберите пункт **Свойства**. Если параметр **Свойства** недоступен, то убедитесь, что среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] запущена с правами администратора.  
  
    4.  Щелкните **Дополнительно**.  
  
    5.  Выберите **EnableClientPrinting**.  
  
    6.  Задайте значение True или False, а затем нажмите кнопку **ОК**.  
  
         ![ssrs_ssmsproperties_clientprinting](../../reporting-services/report-server/media/ssrs-ssmsproperties-clientprinting.png "ssrs_ssmsproperties_clientprinting")  
  
-   Для **сервера отчетов в режиме интеграции с SharePoint**:  
  
    1.  В центре администрирования SharePoint перейдите на страницу **Управление приложением**.  
  
    2.  Выберите **Управление приложениями службы**.  
  
    3.  Щелкните рядом с именем приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , затем нажмите кнопку **Управление** на ленте SharePoint.  
  
    4.  Нажмите кнопку **Системные параметры**.  
  
    5.  Выберите **Включение печати на стороне клиента**. Параметр **Включение печати на стороне клиента** расположен в нижней части страницы.  
  
    6.  Нажмите кнопку **ОК**.  
  
-   Напишите скрипт или код, который устанавливает для системного свойства **EnableClientPrinting** сервера отчетов значение **false.**  
  
 Следующий образец скрипта иллюстрирует один из способов отключения клиентской печати. Скомпилируйте и запустите следующий код [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], чтобы присвоить свойству **EnableClientPrinting** значение **False**. После выполнения кода перезапустите IIS.  
  
### <a name="sample-script"></a>Образец скрипта  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
