---
title: "Развертывание и поддержка версий в SQL Server Data Tools (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Развертывание и поддержка версий в SQL Server Data Tools (SSRS)
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] поддерживает следующие сценарии:  
  
-   Открытые определения отчетов (*RDL) и проекты сервера отчетов (\*RPTPROJ).  
  
-   Создайте определения отчетов.  
  
-   Просмотрите отчеты в конструкторе отчетов.  
  
-   Разверните отчеты на серверах отчетов.  
  
##  <a name="bkmk_ConfigurationandDeploymentProperties"></a> Свойства настройки и развертывания  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] поддерживает конфигурации проекта. Конфигурация проекта состоит из набора свойств, определяющего местоположения и поведения в том случае, когда проект создан в качестве шага просмотра или развертывания отчетов. Дополнительные сведения о конфигурациях проекта см. в документации по Visual Studio.  
  
 Используйте конфигурации проектов, чтобы управлять обновлением определений отчетов до версий схем, совместимых с целевыми серверами отчетов. Конфигурация проекта включает такие свойства, как целевой сервер отчетов, папка, где процесс построения временно сохраняет определения отчетов для предварительного просмотра и развертывания, и уровни ошибок.  
  
 Построение отчетов производится перед подготовкой к просмотру в конструкторе отчетов или развертыванием на сервере отчетов.  
  
 Задать свойства конфигурации можно в диалоговом окне среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **Свойства проекта** .  
  
 Свойства построения и развертывания включают:  
  
-   OutputPath — свойство сборки, показывающее путь к папке для хранения определения отчета, используемого при проверке сборки, развертывании и просмотре отчетов.  
  
-   ErrorLevel — свойство сборки, отображающее серьезность проблем сборки, помечаемых как ошибки. Проблемы, степень серьезности которых меньше значения ErrorLevel или равна ему, выводятся как ошибки. В противном случае они помечаются как предупреждения. Дополнительные сведения см. в подразделе "Проверка отчета и уровни ошибок" раздела [Разработка отчетов с использованием конструктора отчетов (SSRS)](../../reporting-services/tools/design-reports-with-report-designer-ssrs.md).  
  
-   TargetServerVersion — это свойство развертывания, задающее ожидаемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], которая установлена на целевом сервере отчетов, указанном в свойстве TargetServerURL.  
  
 Если указывается более ранняя версия служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в диалоговом окне **Свойства проекта** , отчеты не преобразуются автоматически в предыдущую версию. По сути дела, проект сервера отчетов может содержать отчеты из двух разных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда развертывается проект сервера отчетов, все отчеты в проекте преобразуются в версию, указанную в TargetServerVersion.  
  
 К проекту может быть добавлено более одной конфигурации проекта. Разные конфигурации используются для разных сценариев, например для развертывания в разных версиях серверов отчетов. Дополнительные сведения см. в разделах [Задание свойства развертывания (службы Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md) и [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md).  
  
##  <a name="bkmk_SupportedVersions"></a> Поддерживаемые версии  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], которая является 32-разрядной версией среды разработки проектов сервера отчетов, не предназначена для работы на компьютерах архитектуры [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] и не устанавливается на серверах с архитектурой [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]. Однако имеется поддержка среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] для компьютеров с архитектурой x64.  
  
 В приведенной ниже таблице описаны поддерживаемые версии для создания и публикации отчетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Схема не изменялась после [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
|Тип проекта или файла|Версия|Разработка отчетов|Публикация отчетов|Примечания|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|Проект сервера отчетов<br /><br /> либо<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]|Схема языка определения отчетов версии 2016|[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]||  
|Проект сервера отчетов<br /><br /> либо<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Схема языка определения отчетов версии 2014|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> либо<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Схема языка определения отчетов версии 2012|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> либо<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Схема языка определения отчетов версии 2008 R2|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> либо<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Схема языка определения отчетов версии 2008|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Только сервер отчетов служб|Производит локальное обновление схем языка определения отчетов с версий 2003 и 2005 до версии 2008.|  
  
 Дополнительные сведения об открытии отчетов в предыдущей версии схемы определения отчета см. в разделе [Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md). Дополнительные сведения о конкретных схемах определений отчетов см. в разделе [Спецификация по языку определения отчетов](http://go.microsoft.com/fwlink/?linkid=116865).  
  
## См. также  
 [Публикация источников данных и отчетов](../../reporting-services/reports/publishing-data-sources-and-reports.md)  
  
  