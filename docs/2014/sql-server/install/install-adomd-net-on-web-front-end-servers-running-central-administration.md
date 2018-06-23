---
title: Установите ADOMD.NET на клиентских веб-серверах под управлением центра администрирования | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: ccedd48fcebab07eeb7b27821917b684d98a11d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099929"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Установка ADOMD.NET на веб-серверах, обслуживающих клиентские запросы, под управлением центра администрирования
  При установке PowerPivot для SharePoint в ферму с топологией центра администрирования без служб Excel или PowerPivot для SharePoint загрузите и установите клиентскую библиотеку Microsoft ADOMD.NET, если желаете иметь полный доступ к встроенным на панели управления PowerPivot отчетам. Некоторые отчеты с панели мониторинга используют ADOMD.NET для доступа к внутренним данным, предоставляющим сведения об обработке запросов PowerPivot и исправности сервера в ферме.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Для SharePoint 2013 поставщик включен в пакет дополнительных компонентов SQL Server. Сведения о загрузке spPowerPivot.msi см. в разделе [пакета дополнительных компонентов Microsoft SQL Server 2014](http://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Загрузка и установка клиентской библиотеки  
  
1.  На [страницы пакета дополнительных компонентов SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296473), найдите Microsoft ADOMD.NET.  
  
2.  Загрузите пакет x64 программы установки `SQL_AS_ADOMD.msi`.  
  
3.  Запустите MSI-файл, чтобы установить библиотеку.  
  
4.  По завершении установки сбросьте IIS. Откройте командную строку администратора и введите **IISRESET**.  
  
### <a name="verify-installation"></a>Проверка установки  
  
1.  Перейдите к папке Windows\Assembly.  
  
2.  Щелкните правой кнопкой мыши файл Microsoft.AnalysisServices.AdomdClient и выберите **свойства**.  
  
3.  Нажмите **Версия**.  
  
4.  Убедитесь, что версия содержит 12.00. \<номер построения > и описание Microsoft.analysisservice.adomdclient.  
  
## <a name="see-also"></a>См. также  
 [Панель мониторинга управления PowerPivot и данные об использовании](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  