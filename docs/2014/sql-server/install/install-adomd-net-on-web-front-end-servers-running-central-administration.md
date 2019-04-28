---
title: Установите ADOMD.NET на серверы веб-интерфейса под управлением центра администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cc17daefbe5e84522fdc46ddf046403260ebf4e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659779"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Установка ADOMD.NET на веб-серверах, обслуживающих клиентские запросы, под управлением центра администрирования
  При установке PowerPivot для SharePoint в ферму с топологией центра администрирования без служб Excel или PowerPivot для SharePoint загрузите и установите клиентскую библиотеку Microsoft ADOMD.NET, если желаете иметь полный доступ к встроенным на панели управления PowerPivot отчетам. Некоторые отчеты с панели мониторинга используют ADOMD.NET для доступа к внутренним данным, предоставляющим сведения об обработке запросов PowerPivot и исправности сервера в ферме.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Для SharePoint 2013 поставщик включен в пакет дополнительных компонентов SQL Server. Сведения о загрузке spPowerPivot.msi см. в разделе [пакет дополнительных компонентов Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Загрузка и установка клиентской библиотеки  
  
1.  На [страницы пакета дополнительных компонентов SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296473), найдите Microsoft ADOMD.NET.  
  
2.  Загрузите пакет x64 программы установки `SQL_AS_ADOMD.msi`.  
  
3.  Запустите MSI-файл, чтобы установить библиотеку.  
  
4.  По завершении установки сбросьте IIS. Откройте командную строку администратора и введите **IISRESET**.  
  
### <a name="verify-installation"></a>Проверка установки  
  
1.  Перейдите к папке Windows\Assembly.  
  
2.  Щелкните правой кнопкой мыши файл Microsoft.AnalysisServices.AdomdClient и выберите **свойства**.  
  
3.  Нажмите **Версия**.  
  
4.  Убедитесь, что версия содержит 12.00. \<номер сборки > и описание задано как Microsoft.AnalysisService.AdomdClient.  
  
## <a name="see-also"></a>См. также  
 [Панель мониторинга управления PowerPivot и данные об использовании](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
