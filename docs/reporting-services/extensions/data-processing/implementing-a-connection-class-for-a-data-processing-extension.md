---
title: "Реализация класса Connection для модуля обработки данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 19f059c0041cc9effc48e0db9c4b5ef1a504d020
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>Реализация класса Connection для модуля обработки данных
  **Подключения** представляет подключение к базе данных или аналогичному ресурсу и является отправной точкой для пользователей [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль обработки данных. Он представляет подключения к серверам баз данных, но любая сущность с похожим поведением может быть предоставлен как **соединения**.  
  
 Для реализации **подключения** объекта, можно создать класс, реализующий <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> и при необходимости реализует <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>.  
  
 Перед выполнением команд в реализации следует убедиться, что соединение было создано и открыто. Следует убедиться, что реализация требует от клиентов явного открытия и закрытия соединений, а не выполняет данные операции самостоятельно. После установки соединения следует выполнить проверки безопасности. Настройка необходимости наличия установленного соединения в других классах модуля обработки данных служб [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] поможет обеспечить обязательное выполнение проверок безопасности при работе с источником данных.  
  
 Свойства необходимого соединения представлены в виде строки соединения. Рекомендуется, чтобы в модулях обработки данных служб [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] поддержка свойства <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> осуществлялась с использованием системы пар «имя-значение», определенной в OLE DB.  
  
> [!NOTE]  
>  **Подключение** объектов часто требуется много ресурсов для получения, поэтому необходимо учитывать организации пула соединений или другие методы для решения этой проблемы.  
  
 Интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> наследуется от интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension> следует реализовать в качестве части реализации класса соединения. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension> позволяет классу реализовать локализованное имя модуля и обрабатывать характерные для модуля сведения о конфигурации, хранимые в файле конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Ваш **подключения** объект содержит <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> свойства через его реализацию <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Рекомендуется обеспечить поддержку свойства <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> и модуле обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Это позволит пользователям видеть знакомое локализованное имя модуля в пользовательском интерфейсе (например, в диспетчере отчетов).  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>также позволяет вашей **подключения** объекта для получения и обработки данных пользовательской конфигурации в файле RSReportServer.config. Дополнительные сведения об обработке данных пользовательской конфигурации см. в описании метода <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Класс, реализующий интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension>, не выгружается из памяти при выгрузке остальных классов модуля обработки данных. Таким образом, можно использовать ваш **расширения** для хранения сведений о нескольких соединений или для хранения данных, который может быть кэширован в памяти. Ваш **расширения** класс остается в памяти при условии, что сервер отчетов запущен.  
  
 Вы можете расширить вашей **подключения** класс для поддержки учетных данных в [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] путем реализации <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>. При реализации <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>, и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> свойства <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> включить интерфейс, **встроенной безопасности** флажок и **Username** и **пароль** текстовые поля **источника данных** диалоговое окно в конструкторе отчетов. Это позволяет конструктору отчетов сохранять и получать учетные данные для источников данных, поддерживающих проверку подлинности. Учетные данные хранятся в безопасном месте и используются при подготовке отчетов в режиме предварительного просмотра.  
  
> [!NOTE]  
>  Для скрытой реализации интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> необходимо реализовать члены интерфейсов <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> и <xref:Microsoft.ReportingServices.Interfaces.IExtension>.  
>   
>  Образец **подключения** реализации класса см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
