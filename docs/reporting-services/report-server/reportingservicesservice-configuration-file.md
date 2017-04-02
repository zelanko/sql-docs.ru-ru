---
title: "Файл конфигурации ReportingServicesService | Microsoft Docs"
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
helpviewer_keywords: 
  - "трассировки [службы Reporting Services]"
  - "Служба Windows Report Server, файл конфигурации ReportingServicesService"
  - "ReportingServicesService, файл конфигурации"
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
caps.latest.revision: 41
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 40
---
# Файл конфигурации ReportingServicesService
  Файл ReportingServicesService.exe.config содержит параметры, позволяющие настраивать трассировку.  
  
## Размещение файла  
 Этот файл находится в папке \Reporting Services\Report Server\Bin.  
  
## Рекомендации по изменению  
 В этом файле можно переименовать файл журнала, а также увеличить (или уменьшить) уровень трассировки. Другие параметры изменять не следует. Инструкции см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md). Дополнительные сведения о журналах трассировки см. в разделе [Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
## Пример конфигурации  
 В следующем примере показаны параметры и значения по умолчанию из файла ReportingServicesService.exe.config.  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## Параметры конфигурации  
 Сведения об отдельных параметрах приведены в следующей таблице. Параметры представлены в том порядке, в котором они следуют в файле конфигурации.  
  
|Настройка|Description|  
|-------------|-----------------|  
|**RStrace**|Задает пространства имен для ошибок и трассировки.|  
|**DefaultTraceSwitch**|Задает уровень данных, записываемых в журнал трассировки ReportServerService. Каждый уровень содержит данные, передаваемые более низкими уровнями. Отключать трассировку не рекомендуется. Допустимы следующие значения.<br /><br /> 0 = Отключить трассировку<br /><br /> 1 = Исключения и перезапуски<br /><br /> 2 = Исключения, перезапуски, предупреждения<br /><br /> 3 = Исключения, перезапуски, предупреждения, сообщения о состоянии (по умолчанию)<br /><br /> 4 = Подробный режим|  
|**FileName**|Задает первую часть названия файла журнала. Вторую часть имени определяет значение, заданное в аргументе **Prefix** . По умолчанию это имя ReportServerService_.|  
|**FileSizeLimitMb**|Задает максимальный размер журнала трассировки. Размер измеряется в мегабайтах. Допустимые значения: от 0 до максимально допустимого целого числа. Значение по умолчанию: 32.|  
|**KeepFilesForDays**|Определяет, через сколько дней журнал трассировки будет удален. Допустимые значения: от 0 до максимально допустимого целого числа. Значение по умолчанию: 14.|  
|**Префикс**|Задает формируемое значение, позволяющее отличить один экземпляр журнала от другого. По умолчанию к именам файлов журнала трассировки добавляются значения отметок времени. Значение этой величины — «tid, time». Не изменяйте этот параметр.|  
|**TraceListeners**|Задает, куда будет выводиться содержимое журнала трассировки. Можно через запятую задать несколько расположений. Допустимы следующие значения.<br /><br /> DebugWindow (по умолчанию)<br /><br /> File (по умолчанию)<br /><br /> StdOut|  
|**TraceFileMode**|Определяет, содержат ли журналы трассировки данные за 24-часовой период. Необходимо, чтобы каждому компоненту за каждый день соответствовал один уникальный журнал трассировки. Значение этой величины — Unique (по умолчанию). Не изменяйте это значение.|  
|**Components**|Задает компоненты, для которых создаются журналы трассировки. Значение по умолчанию — **all**. Другими допустимыми значениями этого параметра являются названия внутренних компонентов. Не изменяйте это значение.|  
|**Параметры выполнения**|Задает параметры конфигурации, обеспечивающие обратную совместимость с предыдущей версией. Параметры среды выполнения используются для перенаправления запросов, обращающихся к предыдущей версии пространства имен Microsoft.ReportingServices.Interfaces, в пространство имен новой версии.<br /><br /> Все параметры конфигурации этого раздела описаны в документации по платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Дополнительные сведения можно получить, выполнив поиск по строке «Runtime Schema Settings» на веб-сайте MSDN или в документации по платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .|  
  
## См. также  
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)  
  
  