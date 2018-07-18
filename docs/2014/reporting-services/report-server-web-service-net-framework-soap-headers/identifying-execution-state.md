---
title: Определение состояния выполнения | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 252ec37bb94881a04cfe1137c829274cac6ad893
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330874"
---
# <a name="identifying-execution-state"></a>Определение состояния выполнения
  Протокол HTTP является протоколом без установления соединения и без сохранения состояния. Это означает, что он не может автоматически определить, что различные запросы получены от одного клиента или что один экземпляр браузера продолжает активно просматривать страницу или веб-сайт. Сеансы создают логическое соединение, чтобы сохранять состояние между сервером и клиентом по протоколу HTTP. Сведения конкретного пользователя, относящиеся к определенному сеансу, называются «состоянием сеанса».  
  
 В задачи управления сеансом входит сопоставление HTTP-запроса с предыдущими запросами, созданными в том же сеансе. Без управления сеансом такие запросы оказываются не связанными с веб-службой сервера отчетов, поскольку протокол HTTP по своей природе является протоколом без установления соединения и без сохранения состояния.  
  
 В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не применяется целостный подход к состоянию сеанса, как в [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Однако во время выполнения отчетов сервер отчетов сохраняет состояние между вызовами методов в форме **объекта выполнения**. Объект выполнения позволяет пользователю взаимодействовать с отчетом несколькими способами, включая загрузку отчета с сервера отчетов, задание для отчета учетных данных и параметров и подготовку отчета к просмотру.  
  
 В ходе обмена данными с сервером отчетов клиенты используют объект выполнения для управления просмотром отчетов и переходами пользователей к другим страницам отчета, а также для отображения или скрытия разделов отчета. Для каждого отчета во время работы приложения существует уникальный объект выполнения.  
  
 Обычно время существования объекта выполнения отсчитывается от момента, когда пользователь переходит в браузер или клиентское приложение и выбирает отчет для просмотра. Объект выполнения удаляется после истечения короткого времени ожидания с момента получения последнего запроса на выполнение (по умолчанию время ожидания составляет 20 минут).  
  
 С точки зрения веб-службы время существования отсчитывается от момента, когда вызываются методы <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> или <xref:ReportExecution2005.ReportExecutionService.Render%2A> веб-службы сервера отчетов. Приложение может использовать другие методы для управления активным объектом выполнения (например, для задания параметров и источников данных). Объект выполнения удаляется после истечения короткого времени ожидания с момента получения последнего запроса на выполнение (по умолчанию время ожидания составляет 20 минут).  
  
 Приложение отслеживает несколько активных объектов выполнения между вызовами методов <xref:ReportExecution2005.ReportExecutionService.Render%2A> и <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> веб-службы, сохраняя свойство <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>, которое возвращается в заголовке SOAP из методов <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> и <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.  
  
 На следующей диаграмме показаны пути обработки отчетов и подготовки их к просмотру.  
  
 ![Путь обработки или отрисовки отчета](../../../2014/reporting-services/media/rs-render-process-diagram.gif "Путь обработки или отрисовки отчета")  
  
 Для поддержки описанных выше функций текущий метод Render протокола SOAP был разбит на несколько методов, которые представляют этапы инициализации объекта выполнения, обработки и подготовки к просмотру.  
  
 Чтобы подготовить отчет к просмотру программным образом, необходимо выполнить следующие действия.  
  
-   Загрузите отчет или определение отчета с помощью метода <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> или <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.  
  
-   Определите, нужны ли для отчета учетные данные или параметры, проверив значения свойств <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> и <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> объекта <xref:ReportExecution2005.ExecutionInfo>, возвращенного методом <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> или <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>  
  
-   В случае необходимости задайте учетные данные и параметры с помощью методов <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> и <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A>.  
  
-   Вызовите метод <xref:ReportExecution2005.ReportExecutionService.Render%2A>, чтобы подготовить отчет к просмотру.  
  
 Пока отчет участвует в сеансе, может измениться базовый отчет, хранящийся в базе данных сервера отчетов. Например, может измениться определение отчета, сам отчет может быть удален или перемещен, а также могут измениться разрешения пользователя. Если отчет участвует в активном сеансе, то на него не распространяются изменения, вносимые в базовый отчет (хранящийся в базе данных сервера отчетов).  
  
 Сеансом отчета также можно управлять с помощь команд для доступа по URL-адресу.  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Технический справочник (службы SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)   
 [Использование заголовков SOAP в службах Reporting Services](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
