---
title: Настройка таблицы стилей для просмотра HTML-страниц и диспетчера отчетов | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- style sheets [Reporting Services]
ms.assetid: df805cff-b1de-4062-b2ac-423f37390fbd
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b24525eff885b183b34f5810d79e44e4509e3f06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087798"
---
# <a name="customize-style-sheets-for-html-viewer-and-report-manager"></a>Настройка таблицы стилей для средства просмотра HTML-страниц и диспетчера отчетов
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предоставляет спецификации каскадных таблиц стилей по умолчанию файлы стилей (.css), определяющие стили **отчетов** инструментов в средстве просмотра HTML и для диспетчера отчетов. Веб-разработчик или пользователь, имеющий опыт создания каскадных таблиц стилей, может (на свой страх и риск) модифицировать таблицы стилей по умолчанию, чтобы изменить цвета, шрифты и макет панели инструментов или диспетчер отчетов. В этой версии не документированы ни таблицы стилей по умолчанию, ни инструкции по изменению таблиц стилей.  
  
 Неправильное изменение таблиц стилей может привести к ошибкам при открытии отчетов. Пользователям, сомневающимся в своем умении изменять таблицы стилей, следует использовать таблицы стилей по умолчанию. Если все же решено изменить настройки таблицы стилей, убедитесь, что созданы резервные копии всех файлов CSS, установленных по умолчанию.  
  
 Изменение таблиц стилей не влияет на внешний вид опубликованных отчетов, которые запускаются на сервере отчетов. В службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты не ссылаются на таблицы стилей. Нерегламентированные отчеты, автоматически созданные сервером отчетов, используют сведения о стилях, которые хранятся в виде внедренных ресурсов в программных файлах сервера отчетов. Отчеты, созданные в конструкторе отчетов, используют шрифты, цвета и макет, заданные в определении отчета. Стили создаются на том же уровне, что и остальные элементов макета.  
  
> [!NOTE]  
>  Если нужно использовать предопределенные стили отчета, создайте отчет с помощью мастера отчетов. Мастер отчетов предоставляет разнообразные темы, с помощью которых можно создавать стилизованные отчеты, использующие разные сочетания шрифтов и цветов. Можно изменить шаблоны стилей, определяющих эти темы.  
  
## <a name="reporting-services-style-sheets"></a>Таблицы стилей служб Reporting Services  
 В следующей таблице описаны файлы стилей (CSS), используемых в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] установки.  
  
|Таблица стилей|Описание|  
|-----------------|-----------------|  
|Htmlviewer.css|Образец таблицы стилей, который можно использовать в качестве шаблона для создания собственных таблиц стилей для панели инструментов **Отчет** в средстве просмотра HTML-страниц.<br /><br /> Стили по умолчанию, используемые в средстве просмотра HTML-страниц, внедрены в сервер отчетов. Их образец и содержится в файле Htmlviewer.css.|  
|ReportingServices.css|Определяет стили диспетчера отчетов.|  
  
> [!NOTE]  
>  Следующие таблицы стилей используются в интерактивной документации диспетчера отчетов и не подлежат изменению: Sql.css и Mailto.css. Другие таблицы стилей определяют стили отчетов и диспетчера отчетов, которые открываются в веб-частях SharePoint. Эти таблицы стилей включают Rswebparts.css, Sp_full.css и Sp_small.css. Менять таблицы стилей SharePoint не рекомендуется. Дополнительные сведения об использовании веб-частей см. в разделе [представление и просматривать собственного режима отчеты с помощью веб-частей SharePoint &#40;SSRS&#41;](reports/view-and-explore-native-mode-reports-using-sharepoint-web-parts-ssrs.md).  
  
## <a name="configuring-reporting-services-to-use-a-custom-style-sheet"></a>Настройка служб Reporting Services для использования пользовательской таблицы стилей  
 Таблица стилей должна представлять собой файл допустимой каскадной таблицы стилей (CSS), расположенный в папке Styles. По умолчанию папка Styles находится в \< *диск*>: \Program Files\Microsoft SQL Server\MSSQL. *n*\Reporting Services\ReportServer\Styles.  
  
 Чтобы использовать таблицу стилей для средства просмотра HTML-страниц в режиме реального времени, применяются следующие подходы:  
  
-   Добавьте параметр <`HTMLViewerStyleSheet`> к файлу конфигурации служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   Задайте таблицу стилей в URL-адресе отчета.  
  
### <a name="modifying-the-rsreportserverconfig-file"></a>Изменение файла RSReportServer.config  
 Чтобы задать пользовательскую таблицу стилей для средства просмотра HTML-страниц, можно изменить файл RSReportServer.config. Параметр <`HTMLViewerStyleSheet`> не включен в файл конфигурации по умолчанию. Его необходимо ввести в разделе <`Configuration`> файла RSReportServer.config и задать нужную таблицу стилей. При задании таблицы стилей не указывайте расширение файла CSS.  
  
 В следующем примере показан способ задания таблицы стилей:  
  
```  
<Configuration>  
...  
          <HTMLViewerStyleSheet>MyStyleSheet</HTMLViewerStyleSheet>  
...  
</Configuration>  
```  
  
### <a name="specifying-a-style-sheet-on-a-report-url"></a>Указание таблицы стилей в URL-адресе отчета  
 Для задания пользовательской таблицы стилей в URL-адресе отчета можно использовать параметр доступа `rc:StyleSheet`. Дополнительные сведения об указании параметров доступа URL-адреса см. в разделе [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
 В следующем примере показан способ добавления пользовательских стилей:  
  
```  
http://localhost/reportserver?/AdventureWorksSampleReports/Product+Line+Sales&rs:Command=Render&rc:Stylesheet=MyStyleSheet  
```  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отчетов &#40;собственный режим служб SSRS&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Просмотра HTML-страниц и панель инструментов отчета](html-viewer-and-the-report-toolbar.md)   
 [Файл конфигурации RSReportServer](report-server/rsreportserver-config-configuration-file.md)  
  
  