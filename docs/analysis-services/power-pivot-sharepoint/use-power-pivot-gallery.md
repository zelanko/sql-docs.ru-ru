---
title: "Использование коллекции PowerPivot | Документы Microsoft"
ms.custom: 
ms.date: 08/31/2015
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ff92d1-787a-4f34-990f-6676b61875d7
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c6397bfd177a5d5901fdda29f4b34c9f6b7ffa7d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="use-power-pivot-gallery"></a>Использование коллекции PowerPivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Коллекция — это специальная библиотека документов SharePoint, которая предоставляет широкие возможности просмотра и управления документами для опубликованных книг Excel и отчетов служб Reporting Services, содержащих [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] данных.  
  
> [!NOTE]  
>  В зависимости от конфигурации сервера в области предварительного просмотра для некоторых документов могут появляться предупреждения или сообщения об ошибках. Сообщения могут появляться, если для книги Excel задано автоматическое обновление данных при открытии. Сообщения с предупреждениями об обновлении данных отображаются в изображении предварительного просмотра, если в службе Excel настроена выдача таких предупреждений. Администратор фермы или службы может изменить параметры конфигурации, включив показ фактических листов при предварительном просмотре. Дополнительные сведения см. в разделе [Создание надежного расположения для сайтов PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
##  <a name="bkmk_top"></a> В этом разделе  
 [Предварительные требования](#prereq)  
  
 [Значки в коллекции PowerPivot](#icons)  
  
 [Сохранение книги Excel в коллекции PowerPivot](#add)  
  
 [Создание новых отчетов или книг на основе опубликованной книги PowerPivot](#newdocs)  
  
 [Открыть книгу или отчет в полностраничном режиме](#view)  
  
 [Планирование обновления данных для книг PowerPivot в коллекции PowerPivot](#newdr)  
  
 [Удаление книги или отчета из коллекции PowerPivot](#delete)  
  
 [Обновление эскиза](#image)  
  
 [Известные проблемы](#bkmk_known_issues)  
  
##  <a name="prereq"></a> Предварительные требования  
  
> [!NOTE]  
>  Для коллекции Power Pivot требуется Microsoft Silverlight.  Браузер Microsoft Edge не поддерживает Silverlight.   
> Чтобы просмотреть содержание библиотеки в Edge, щелкните вкладку **Библиотека** в коллекции Power Pivot, а затем измените представление библиотеки документов на **Все документы**.    
> Чтобы изменить представление по умолчанию, щелкните вкладку **Библиотека** и щелкните "Изменить представление". Щелкните "Сделать представлением по умолчанию", а затем "ОК", чтобы сохранить представление по умолчанию.  
>  Дополнительную информацию о том, что поддерживается в Edge, см. в статье блога Windows [Побег из прошлого, часть 2: прощание с ActiveX, VBScript...](https://blogs.windows.com/msedgedev/2015/05/06/a-break-from-the-past-part-2-saying-goodbye-to-activex-vbscript-attachevent/)  
  
 Полный список предварительных требований см. в статье [Create and Customize Power Pivot Gallery](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md).  
  
##  <a name="icons"></a> Значки в коллекции PowerPivot  
 Значки являются визуальным индикатором наличия контекста и состояния.  
  
|Значок|Description|  
|----------|-----------------|  
|![GMNI_PowerPivotGalleryIcon_Hourglass](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-hourglass.gif "GMNI_PowerPivotGalleryIcon_Hourglass")|Значок песочных часов появляется во время формирования эскиза каждой страницы документа. Обновите страницу, чтобы отобразить обновленное изображение.|  
|![GMNI_PowerPivotGalleryIcon_Truncated](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-truncated.gif "GMNI_PowerPivotGalleryIcon_Truncated")|Значок страниц появляется в тот момент, когда количество страниц книги или отчета превышает максимальное количество страниц, которое может быть отображено в коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Для просмотра всех страниц необходимо пользоваться клиентским приложением.|  
|![GMNI_PowerPivotGalleryIcon_Error](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-error.gif "GMNI_PowerPivotGalleryIcon_Error")|Значок ошибки появляется в том случае, если не удалось отобразить эскиз документа. Документ публикуется в библиотеке, однако его не удается преобразовать для просмотра в пользовательских представлениях коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . При этом его можно будет открыть в таких клиентских приложениях, как надстройка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel.|  
|![GMNI_PowerPivotGalleryIcon_badtype](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-badtype.gif "GMNI_PowerPivotGalleryIcon_badtype")|Значок недоступного содержимого открывается, когда загруженный документ невозможно преобразовать для просмотра в коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Поддерживаются следующие типы документов: книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и отчеты, созданные в построителе отчетов служб SQL Server 2008 R2 Reporting Services.<br /><br /> Этот значок также появляется при восстановлении документа из корзины.<br /><br /> Если этот значок появляется для документа, который раньше представлял собой допустимое изображение предварительного просмотра, изображение можно обновить, изменив свойство документа и сохранив изменения.|  
|![GMNI_PowerPivotGalleryIcon_Locked](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")|Значок заблокированного содержимого появляется в тот момент, когда отображение эскизов для этого документа преднамеренно отключено. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] не создает эскизы для книг Excel, которые не содержат данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , а также для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и отчетов Reporting Services, которые не соответствуют требованиям к формированию моментальных снимков. Дополнительные сведения см. в подразделе «Предварительные условия» в этом разделе.|  
  
##  <a name="add"></a> Сохранение книги Excel в коллекции PowerPivot  
 Книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] можно опубликовать в библиотеке с помощью любых методов совместного доступа, имеющихся в Excel 2010. Например, в Excel 2010 при выполнении команды «Сохранить как» путь SharePoint к библиотеке можно указать полностью или частично.  
  
1.  Сохраните файл.  
  
2.  1.  **Excel 2010**: в меню "Файл" выберите **Сохранить и отправить**.  
  
    2.  Выберите операцию **Сохранить в SharePoint**.  
  
    3.  Если для выбора отдельных публикуемых листов или параметров требуется использовать параметры служб Excel, выберите **Параметры публикации** . Например, вкладка «Параметры» в параметрах служб Excel позволяет выбрать, какие срезы будут выводиться в опубликованной книге.  
  
    1.  **Excel 2013**  : в меню "Файл" выберите **Сохранить**.  
  
    2.  Для выбора отдельных публикуемых листов или параметров требуется использовать параметры служб Excel, выберите **Параметры представления браузера** . Например, вкладка «Параметры» в параметрах служб Excel позволяет выбрать, какие срезы будут выводиться в опубликованной книге.  
  
3.  В поле имени файла диалогового окна «Сохранить как» введите полный или частичный URL-адрес коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Если введена часть URL-адреса, например имя сервера, можно просмотреть сайт, чтобы найти галерею [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Для этого нажмите **Сохранить** , чтобы установить соединение с указанным сервером.  
  
     ![GMNI_ExcelSaveAs](../../analysis-services/power-pivot-sharepoint/media/gmni-excelsaveas.gif "GMNI_ExcelSaveAs")  
  
1.  В диалоговом окне «Сохранить как» выберите галерею [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на вашем сайте.  
  
2.  Нажмите кнопку **Открыть** , чтобы открыть библиотеку.  
  
3.  Нажмите кнопку **Сохранить** , чтобы опубликовать книгу в библиотеке.  
  
 В окне браузера убедитесь, что документ выводится в галерее [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Новые опубликованные документы появятся в списке. Параметры библиотеки определяют место размещения документов (например, они будут отсортированы в порядке возрастания по дате или в алфавитном порядке по имени). Возможно, понадобится обновить окно браузера, чтобы отобразить самые последние добавления.  
  
#### <a name="upload-a-workbook-into-power-pivot-gallery"></a>Передача книги в коллекцию PowerPivot  
 Можно также передать книгу, если вы хотите начать с SharePoint и выбрать на компьютере файл для публикации.  
  
1.  На сайте SharePoint откройте коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
2.  На ленте библиотеки выберите **Документы**.  
  
3.  В меню **Передача документа**выберите параметр передачи и укажите имя и расположение файла, который необходимо передать. Параметры библиотеки определяют, где появляется документ. Возможно, понадобится обновить окно браузера для просмотра самых последних добавлений.  
  
##  <a name="newdocs"></a> Создание новых отчетов или книг на основе опубликованной книги PowerPivot  
 Для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , которые публикуются в Галерее [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , можно создавать дополнительные книги или отчеты служб Reporting Services, использующие опубликованную книгу в качестве подключенного источника данных.  
  
|||  
|-|-|  
|![GMNI_btn_NewDocReportGallery](../../analysis-services/power-pivot-sharepoint/media/gmni-btn-newdocreportgallery.gif "GMNI_btn_NewDocReportGallery")|Нажмите часть кнопки «Создать отчет» со стрелкой вниз, чтобы запустить построитель отчетов или Excel 2010. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Чтобы кнопка "Создать отчет" стала доступной, в коллекции необходимо использовать одно из стандартных представлений ("Театр", "Коллекция" или "Карусель").|  
  
#### <a name="create-report-builder-report"></a>Создание отчета построителя отчетов  
 Для создания нового отчета, основанного на существующей книге [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в библиотеке, требуется, чтобы службы Reporting Services были настроены для интеграции с SharePoint для сайтов, которые содержат коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . При выборе варианта «Создать отчет построителя отчетов» с сервера отчетов загружается построитель отчетов, который устанавливается на локальной рабочей станции при первом использовании. Для нового отчета создается файл-заполнитель отчета, который сохраняется в коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Сведения о подключении к книге [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] создаются как новый источник данных в отчете. На следующем шаге в рабочей области конструктора можно создать наборы данных и макет отчета. При использовании построителя отчетов для сборки отчета изменения и окончательные результаты можно сохранить в документе отчета в галерее. Чтобы в будущем не допустить разрыва связей между данными, необходимо хранить файлы отчета и книги в одной библиотеке.  
  
#### <a name="open-new-excel-workbook"></a>Открыть новую книгу Excel  
 Чтобы создать новую книгу Excel из существующей, на локальном компьютере должны быть установлены Excel и клиент [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] . При выборе команды "Открыть новую книгу Excel" запускается Excel, открывается пустой файл книги (XLSX) и в качестве подключенного источника данных в фоновом режиме загружаются данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . В новой книге используются только данные из окна [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в исходной книге. Сводные таблицы или сводные диаграммы из исходной книги исключаются. Новая книга ссылается на данные исходной книги. Данные не копируются в саму новую книгу.  
  
##  <a name="view"></a> Открыть книгу или отчет в полностраничном режиме  
 Щелкните любой видимый эскиз просматриваемого документа, чтобы открыть его в полностраничном режиме отдельно от предварительного просмотра галереи [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] открываются в браузере. Отчеты Reporting Services откроются в веб-части ReportViewer, являющейся частью развернутой службы Reporting Services на сервере SharePoint.  
  
 Вместо просмотра книги в браузере можно открыть книгу в Excel на клиентской рабочей станции. Для просмотра файла необходимы Excel 2013 или Excel 2010 и надстройка [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] . В Excel 2007 можно открыть файл, но нельзя использовать Excel 2007 для сведения данных. Поэтому для просмотра и создания данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] рекомендуется использовать Excel 2013 или Excel 2010. Если у вас нет нужных приложений, необходимо использовать браузер для просмотра книги из SharePoint.  
  
##  <a name="newdr"></a> Планирование обновления данных для книг PowerPivot в коллекции PowerPivot  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в опубликованной книге Excel можно обновлять через запланированные интервалы.  
  
|||  
|-|-|  
|![GMNI_btn_NewDataRefreshReportGallery](../../analysis-services/power-pivot-sharepoint/media/gmni-btn-newdatarefreshreportgallery.gif "GMNI_btn_NewDataRefreshReportGallery")|Нажмите кнопку «Управление обновлением данных», чтобы создать или просмотреть расписание получения обновленных данных из подключенных источников данных. Дополнительные сведения о создании расписания см. в разделе [Планирование обновления данных (PowerPivot для SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b).|  
  
##  <a name="delete"></a> Удаление книги или отчета из коллекции PowerPivot  
 Чтобы удалить документ из библиотеки, сначала нужно переключиться на представление «Все документы».  
  
1.  На сайте SharePoint откройте коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
2.  На ленте нажмите кнопку **Библиотека**.  
  
3.  В области «Управление представлениями» в списке текущих представлений нажмите стрелку вниз и выберите «Все документы».  
  
4.  Выберите книгу или отчет, которые хотите удалить.  
  
5.  В области "Документы (файлы)" в разделе "Управление" нажмите кнопку **Удалить документ** .  
  
##  <a name="image"></a> Обновление эскиза  
 Чтобы повторно создать эскиз документа в коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , сделайте следующее.  
  
1.  Переключите коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в представление "Все документы". Для этого выберите пункт **Библиотека** на ленте и измените **Текущее представление** на **Все документы**.  
  
2.  Выберите книгу или отчет, для которого нужно обновить эскиз.  
  
3.  Нажмите стрелку вниз справа и выберите **Изменить свойства**.  
  
4.  Нажмите кнопку **Сохранить**. При сохранении документа служба моментальных снимков выполняет повторное создание эскиза.  
  
##  <a name="bkmk_known_issues"></a> Известные проблемы  
  
### <a name="document-type-is-not-supported"></a>Тип документа не поддерживается  
 Тип содержимого **Документ коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** не поддерживается. Если включить тип содержимого **Документ коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** для библиотеки документов и попытаться создать новый документ этого типа, появится сообщение об ошибке, похожее на следующее:  
  
-   «Создать документ» требует приложение, совместимое с Microsoft Sharepoint Foundation, и веб-браузер. Чтобы добавить документ в эту библиотеку документов, нажмите кнопку «Передача документа».  
  
-   «Адрес в Интернете http://[server name]/testSite/PowerPivot Gallery/ReportGallery/Forms/Template.xlsx недействителен». «Microsoft Excel не может получить доступ к файлу http://[server name]/testSite/PowerPivot Gallery/ReportGallery/Forms/Template.xlsx». Существует несколько возможных причин.  
  
 Тип содержимого **Документ коллекции [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** не добавляется автоматически в библиотеки документов. Вы не столкнетесь с этой проблемой, если вручную не включите неподдерживаемый тип содержимого.  
  
## <a name="see-also"></a>См. также:  
 [Создание надежного расположения для сайтов PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [Удаление коллекции Power Pivot](../../analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery.md)   
 [Создание и настройка коллекции Power Pivot](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)   
 [Планирование обновления данных (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
  
