---
title: Реализация класса Connection для модуля обработки данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fbd293c156f373de0cdad53b4419633ded15af8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63164129"
---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>Реализация класса Connection для модуля обработки данных
  Объект **Connection** представляет подключение к базе данных или аналогичному ресурсу. Он является начальной точкой для пользователей модуля обработки данных служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Он представляет собой соединения с серверами баз данных, хотя, в принципе, любая сущность с похожим поведением может быть представлена как **Connection**.  
  
 Для реализации объекта **Connection** следует создать класс, реализующий интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> и (необязательно) интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>.  
  
 Перед выполнением команд в реализации следует убедиться, что соединение было создано и открыто. Следует убедиться, что реализация требует от клиентов явного открытия и закрытия соединений, а не выполняет данные операции самостоятельно. После установки соединения следует выполнить проверки безопасности. Настройка необходимости наличия установленного соединения в других классах модуля обработки данных служб [!INCLUDE[ssRS](../../../includes/ssrs.md)] поможет обеспечить обязательное выполнение проверок безопасности при работе с источником данных.  
  
 Свойства необходимого соединения представлены в виде строки соединения. Рекомендуется, чтобы в модулях обработки данных служб [!INCLUDE[ssRS](../../../includes/ssrs.md)] поддержка свойства <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> осуществлялась с использованием системы пар «имя-значение», определенной в OLE DB.  
  
> [!NOTE]  
>  Получение объектов **Connection** связано с затратами ресурсов; для компенсации рекомендуется использовать метод организации пула соединений или другие методики.  
  
 Интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> наследуется от интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension> следует реализовать в качестве части реализации класса соединения. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension> позволяет классу реализовать локализованное имя модуля и обрабатывать характерные для модуля сведения о конфигурации, хранимые в файле конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Объект **Connection** содержит свойство <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> из-за реализации интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Рекомендуется обеспечить поддержку свойства <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> и модуле обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Это позволит пользователям видеть знакомое локализованное имя модуля в пользовательском интерфейсе (например, в диспетчере отчетов).  
  
 Интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension> также позволяет объекту **Connection** получать и обрабатывать данные пользовательской конфигурации, хранимые в файле RSReportServer.config. Дополнительные сведения об обработке данных пользовательской конфигурации см. в описании метода <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Класс, реализующий интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension>, не выгружается из памяти при выгрузке остальных классов модуля обработки данных. В связи с этим класс **Extension** можно использовать для хранения данных о состоянии, действительных для нескольких соединений, или для хранения данных, которые могут быть кэшированы в памяти. Класс **Extension** остается в памяти, пока запущен сервер отчетов.  
  
 Класс **Connection** можно расширить, добавив в службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] поддержку учетных данных, реализовав интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>. При реализации свойств <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> в диалоговом окне **Источник данных** в конструкторе отчетов включается поле для флажка **Интегрированная безопасность** и текстовые поля **Имя пользователя** и **Пароль**. Это позволяет конструктору отчетов сохранять и получать учетные данные для источников данных, поддерживающих проверку подлинности. Учетные данные хранятся в безопасном месте и используются при подготовке отчетов в режиме предварительного просмотра.  
  
> [!NOTE]  
>  Для скрытой реализации интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> необходимо реализовать члены интерфейсов <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> и <xref:Microsoft.ReportingServices.Interfaces.IExtension>.  
>   
>  Образец реализации класса **Connection** см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Реализация модуля обработки данных](implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
