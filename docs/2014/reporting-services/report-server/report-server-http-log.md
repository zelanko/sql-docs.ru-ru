---
title: Журнал HTTP-запросов сервера отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTTP [Reporting Services]
ms.assetid: 6cc433b7-165c-4b16-9034-79256dd6735f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 9eb3cd35267075b6228df993f31dbec021b681bf
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031375"
---
# <a name="report-server-http-log"></a>Журнал HTTP-запросов сервера отчетов
  В файлах журнала HTTP сервера отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] хранится информация для каждого HTTP-запроса и ответа, обработанного сервером отчетов. Сообщения об ошибках, связанных с переполнением очереди запросов и временем ожидания, не достигают сервера отчетов, поэтому не регистрируются в файле журнала.  
  
 По умолчанию ведение журнала HTTP не включено. Чтобы включить ведение журнала HTTP, измените файл конфигурации **ReportingServicesService.exe.config** для использования этой функции в своей установке.  
  
## <a name="viewing-log-information"></a>Просмотр данных журнала  
 Журнал представляет собой текстовый ASCII-файл. Просмотреть этот файл можно в любом текстовом редакторе. Файл журнала HTTP сервера отчетов эквивалентен расширенному файлу журнала W3C в службах IIS, и в нем используются аналогичные поля, что позволяет применять существующие средства просмотра журнала IIS для чтения файлов журнала HTTP сервера отчетов. В следующей таблице содержатся дополнительные сведения о файле журнала HTTP.  
  
|||  
|-|-|  
|**Имя файла**|Имена файлов журнала по умолчанию:<br /><br /> `ReportServerService_HTTP_<timestamp>.log.`<br /><br /> Можно задать другой префикс имени файла, изменив атрибут HttpTraceFileName в файле конфигурации ReportingServicesService.exe.config. Отметки времени создаются на основе времени по Гринвичу (UTC).|  
|**Размещение файла**|Файлы записываются в следующую папку:<br /><br /> `\Microsoft SQL Server\<SQL Server Instance>\Reporting Services\LogFiles`|  
|**Формат файла**|Этот файл имеет формат EN-US. Он представляет собой текстовый ASCII-файл.|  
|**Создание и хранение файла**|Журнал HTTP создается после его включения в файле конфигурации, перезапуска службы и обработки сервером отчетов HTTP-запроса. Если необходимые параметры были настроены, но файл журнала отсутствует, откройте какой-либо отчет или запустите одно из приложений сервера отчетов (например, диспетчер отчетов), чтобы был сформирован HTTP-запрос для создания этого файла.<br /><br /> После каждого перезапуска службы и последующего HTTP-запроса на сервер отчетов создается новый экземпляр файла журнала.<br /><br /> По умолчанию размер журналов трассировки ограничен 32 МБ, а срок их хранения — 14 дней.|  
  
## <a name="configuration-settings-for-report-server-http-log"></a>Параметры конфигурации для журнала HTTP сервера отчетов  
 Чтобы настроить конфигурацию журнала HTTP-сервера отчетов, измените файл **ReportingServicesService.exe.config** с помощью программы "Блокнот". Этот файл конфигурации находится в папке \Program Files\Microsoft SQL Server\MSSQL.n\Reporting Services\ReportServer\Bin.  
  
 Чтобы разрешить применение сервера HTTP, добавьте запись `http:4` в раздел RStrace файла ReportingServicesService.exe.config. Все другие записи файла журнала HTTP являются необязательными. Следующий пример содержит все параметры, так что можно вставить целый раздел над разделом RStrace, а затем удалить ненужные параметры.  
  
```  
   <RStrace>  
         <add name="FileName" value="ReportServerService_" />  
         <add name="FileSizeLimitMb" value="32" />  
         <add name="KeepFilesForDays" value="14" />  
         <add name="Prefix" value="tid, time" />  
         <add name="TraceListeners" value="debugwindow, file" />  
         <add name="TraceFileMode" value="unique" />  
         <add name="HttpTraceFileName" value="ReportServerService_HTTP_" />  
         <add name="HttpTraceSwitches" value="date,time, clientip,username,serverip,serverport,host,method,uristem,uriquery,protocolstatus,bytesreceived,timetaken,protocolversion,useragent,cookiereceived,cookiesent,referrer" />  
         <add name="Components" value="all:3,http:4" />  
   </RStrace>  
```  
  
## <a name="log-file-fields"></a>Поля файла журнала  
 В следующей таблице описаны поля, доступные в журнале. Список полей можно изменить. С помощью параметра конфигурации `HTTPTraceSwitches` можно указать, какие поля необходимо включить. **По умолчанию** столбца указывает ли поле будет включаться в файл журнала автоматически, если вы не укажете `HTTPTraceSwitches`.  
  
|Поле|Описание|Значение по умолчанию|  
|-----------|-----------------|-------------|  
|HttpTraceFileName|Это значение является необязательным. Значением по умолчанию является ReportServerServiceHTTP_. Можно указать другое значение, если требуется использовать другое соглашение об именах (например, чтобы включить имя сервера, если файлы журналов сохраняются в каком-то централизованном расположении).|Да|  
|HTTPTraceSwitches|Это значение является необязательным. Если указан этот параметр, можно настроить поля, используемые в файле журнала, в формате с разделителями-запятыми.|Нет|  
|Дата|Дата, когда произошло действие.|Нет|  
|Time|Время, в которое произошло указанное действие.|Нет|  
|ClientIp|IP-адрес клиента, получающего доступ к серверу отчетов.|Да|  
|UserName|Имя пользователя, который получил доступ к серверу отчетов.|Нет|  
|ServerPort|Номер порта, используемого для соединения.|Нет|  
|Узел|Содержимое заголовка узла.|Нет|  
|Метод|Действие или метод SOAP, вызванный из клиентского приложения.|Да|  
|UriStem|Ресурс, к которому получен доступ.|Да|  
|UriQuery|Запрос, использованный для доступа к ресурсу.|Нет|  
|ProtocolStatus|Код состояния HTTP.|Да|  
|BytesReceived|Число байт, полученных сервером.|Нет|  
|TimeTaken|Время (в миллисекундах), прошедшее с момента возврата компонентом HTTP.SYS данных запроса до завершения последней отправки сервером, в которое не входит время передачи по сети.|Нет|  
|ProtocolVersion|Версия протокола, используемого клиентом.|Нет|  
|UserAgent|Тип браузера, используемый клиентом.|Нет|  
|CookieReceived|Содержимое куки-файла, полученного сервером.|Нет|  
|CookieSent|Содержимое куки-файла, отправленного сервером.|Нет|  
|Referrer|Предыдущий сайт, посещенный клиентом.|Нет|  
  
## <a name="see-also"></a>См. также  
 [Журнал трассировки службы сервера отчетов](report-server-service-trace-log.md)   
 [Файлы и источники журналов служб Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
