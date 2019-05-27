---
title: Файл конфигурации RSReportDesigner | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5ba4168f5417260b0857accdb9cf8fb3fa0f3c0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66103339"
---
# <a name="rsreportdesigner-configuration-file"></a>RSReportDesigner, файл конфигурации
  Файл конфигурации RSReportDesigner.config хранит параметры подготовки отчета и модулей обработки данных, доступных конструктору отчетов. Сведения о модуле обработки данных хранятся в элементе `Data`. Сведения о модуле обработки данных хранятся в элементе `Render`. Элемент `Designer` перечисляет построители запросов, используемые в конструкторе отчетов.  
  
 Конструктор отчетов использует такую функцию сервера, как внедренный отчет, для предварительного просмотра отчетов. Серверные установки могут быть указаны для поддержки предварительного просмотра операций на стороне местного сервера. Дополнительные сведения о параметрах конфигурации сервера отчетов см. в разделе [файл конфигурации RSReportServer](rsreportserver-config-configuration-file.md).  
  
## <a name="file-location"></a>Размещение файла  
 Этот файл находится в каталоге \Program Files\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies.  
  
## <a name="editing-guidelines"></a>Рекомендации по изменению  
 Не изменяйте параметры в этом файле, кроме случаев, когда это необходимо для развертывания или удаления пользовательского модуля, отключения кэширования во время предварительного просмотра или регистрации нового модуля обработки данных после установки пакета обновления.  
  
 Для настройки параметров модуля подготовки отчетов доступны специальные инструкции по изменению файлов конфигурации. Дополнительные сведения см. в разделе [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
 Общие инструкции по изменению файлов конфигурации см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="example-configuration-file"></a>Пример файла конфигурации  
 Следующий пример иллюстрирует формат файла RSReportDesigner.config.  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a>Параметры конфигурации  
  
|Параметр|Описание|  
|-------------|-----------------|  
|`SecureConnectionLevel`|Определяет уровень безопасности подключения в веб-службе. Диапазон допустимых значений от 0 до 3, где 0 — минимальный уровень. Дополнительные сведения см. в статье [Using Secure Web Service Methods](../report-server-web-service/net-framework/using-secure-web-service-methods.md).|  
|`InstanceName`|Идентификатор сервера предварительного просмотра. Не изменяйте это значение.|  
|`SessionCookies`|Указывает, использует ли сервер отчетов куки-файлы браузера для сохранения сведений о сеансах. Допустимые значения включают `true` и `false`. Значение по умолчанию — `true`. Если значение указано как false, данные о сеансе настройки хранятся в базе данных **reportservertempdb** .|  
|`SessionTimeoutMinutes`|Указывает период, в течение которого для сеанса действительны куки-файлы. Значение по умолчанию равно 3 минутам.|  
|`PolicyLevel`|Определяет файл конфигурации политики безопасности. Допустимым значением является Rspreviewpolicy.config. Дополнительные сведения см. в разделе [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|  
|`CacheDataForPreview`|При установке значения `True` конструктор отчетов сохраняет данные в кэш-файле на локальном компьютере. Допустимые значения `True` (по умолчанию) и `False`. Дополнительные сведения см. в статье [Previewing Reports](../reports/previewing-reports.md).|  
|`Render`|Перечисляет модули предварительного просмотра, доступные конструктору отчетов для организации предварительного просмотра. Набор модулей подготовки отчетов, используемых для предварительного просмотра, должен совпадать с набором, установленным сервером отчетов.<br /><br /> `Name` указывает модуль предварительного просмотра. Если модуль предварительного просмотра вызывается через код, используйте это значение для вызова определенного модуля.<br /><br /> `Type` задает полное имя класса для класса модуля, а также дополнительно имя библиотеки, разделенные запятыми.<br /><br /> `Visible` указывает, появляется ли имя в каком-либо из пользовательских интерфейсов. Значение может быть `True` (по умолчанию) или `False`. Если `True`, оно появляется в пользовательском интерфейсе.|  
|`Data`|Перечисляет модули обработки данных, доступные конструктору отчетов для подключения к источникам данных, которые предоставляют данные для отчетов. Набор модулей предварительного просмотра, используемых конструктором отчетов, может совпадать с набором, установленным сервером отчетов. При добавлении или удалении пользовательского модуля см. раздел [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).<br /><br /> `Name` указывает модуль обработки данных.<br /><br /> `Type` задает полное имя класса для класса модуля, а также дополнительно имя библиотеки, разделенные запятыми.|  
|`Designer`|Перечисляет построители запросов, доступные конструктору отчетов. Построители запросов предоставляют пользовательский интерфейс для конструирования запросов, которые извлекают данные, используемые в отчетах. Построители запросов могут меняться для разных модулей обработки данных. По умолчанию службы Reporting Services предоставляют один пользовательский интерфейс для визуальных средств для всех включенных в продукт модулей обработки данных. Однако если происходит построение или использование модулей обработки данных, предоставленных сторонними поставщиками, может быть применен другой интерфейс построителя запросов.|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|Указывает длительность ожидания запуска службы обработки предварительного просмотра, по истечении которого отображается сообщение об ошибке. Значение по умолчанию составляет 15 секунд.|  
  
## <a name="see-also"></a>См. также  
 [Файлы конфигурации служб Reporting Services](reporting-services-configuration-files.md)   
 [Средства проектирования в отчет конструктора SQL Server Data Tools запросов &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)  
  
  
