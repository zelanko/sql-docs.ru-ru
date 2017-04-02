---
title: "Техническая версия отчетов Power&#160;BI в SSRS&#160;— заметки о выпуске | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f20d7-a9f9-47e3-8dc3-c544a14457e0
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Заметки о выпуске служб Reporting Services
 ||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]** Техническая версия отчетов Power BI в службах SQL Server Reporting Services (январь 2017 г.)|

В этой статье описываются ограничения и проблемы, связанные с технической версией отчетов Power BI в службах SQL Server Reporting Services.

- Сведения о новых возможностях этого выпуска см. в статье [Новые возможности служб Reporting Services (SSRS)](../reporting-services/новые-возможности-служб-sql-server-reporting-services-ssrs.md).

 **Попробуйте продукт:**    
   -   [![Скачать из Центра загрузки Майкрософт](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?linkid=839351) Скачайте техническую версию отчетов Power BI в службах SQL Server Reporting Services и Power BI Desktop (службы SQL Server Reporting Services) из **[центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=839351)**.


## <a name="january--2017"></a>Январь 2017 г.

### <a name="report-server"></a>Сервер отчетов

- Теперь поддерживается протокол HTTPS. Он не был доступен в технической версии виртуальной машины, выпущенной в октябре 2016 г. Дополнительные сведения см. в разделе [Настройка соединений SSL для сервера отчетов, работающего в собственном режиме](../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).
   - Протокол HTTPS необходим для использования надстройки веб-средства просмотра PowerPoint и для вывода в нем отчетов Power BI.
- Теперь поддерживается масштабирование. Оно не было доступно в технической версии виртуальной машины, выпущенной в октябре 2016 г. Дополнительные сведения см. в статье [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../reporting-services/install-windows/configure a native mode report server scale-out deployment.md).

### <a name="power-bi-reports"></a>Отчеты Power BI

- Для использования со службами SQL Server Reporting Services отчеты Power BI следует создавать с помощью Power BI Desktop (службы SQL Server Reporting Services). Приложение Power BI Desktop (службы SQL Server Reporting Services) можно скачать из центра оценки.
- Отчеты Power BI поддерживают только активные подключения к службам Analysis Services (табличные или многомерные).
- Поддержка пользовательских визуальных элементов отсутствует.
- Поддержка визуальных элементов R отсутствует.