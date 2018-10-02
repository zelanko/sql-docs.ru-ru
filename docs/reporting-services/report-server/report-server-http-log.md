---
title: Журнал HTTP-запросов сервера отчетов | Документы Майкрософт
ms.date: 03/02/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- HTTP [Reporting Services]
ms.assetid: 6cc433b7-165c-4b16-9034-79256dd6735f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 85e0bf1588739c5e27ec46273ad1a24908639c14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789952"
---
# <a name="report-server-http-log"></a>Журнал HTTP-запросов сервера отчетов
  В файле журнала HTTP сервера отчетов хранится информация для каждого HTTP-запроса и ответа, обработанного сервером отчетов. Сообщения об ошибках, связанных с переполнением очереди запросов и временем ожидания, не достигают сервера отчетов, поэтому не регистрируются в файле журнала.  
  
 По умолчанию ведение журнала HTTP не включено. Необходимо изменить файл конфигурации ReportingServicesService.exe, чтобы использовать эту функцию в своей установке.  
  
## <a name="viewing-log-information"></a>Просмотр данных журнала  
 Журнал представляет собой текстовый ASCII-файл. Просмотреть этот файл можно в любом текстовом редакторе. Файл журнала HTTP сервера отчетов эквивалентен расширенному файлу журнала W3C в службах IIS, и в нем используются аналогичные поля, что позволяет применять существующие средства просмотра журнала IIS для чтения файлов журнала HTTP сервера отчетов. В следующей таблице содержатся дополнительные сведения о файле журнала HTTP.  
  
|||  
|-|-|  
|Имя файла|По умолчанию этот файл имеет имя ReportServerService_HTTP_\<отметка_времени>.log. Можно задать другой префикс имени файла, изменив атрибут HttpTraceFileName в файле конфигурации ReportingServicesService.exe.config. Отметки времени создаются на основе времени по Гринвичу (UTC).|  
|Размещение файла|Этот файл расположен в папке \Microsoft SQL Server\\*\<экземпляр SQL Server>* \Reporting Services\LogFiles.|  
|Формат файла|Этот файл имеет формат EN-US. Он представляет собой текстовый ASCII-файл.|  
|Создание и хранение файла|Журнал HTTP создается после его включения в файле конфигурации, перезапуска службы и обработки сервером отчетов HTTP-запроса. Если необходимые параметры были настроены, но файл журнала отсутствует, откройте какой-либо отчет или запустите одно из приложений сервера отчетов (например, диспетчер отчетов), чтобы был сформирован HTTP-запрос для создания этого файла.<br /><br /> После каждого перезапуска службы и последующего HTTP-запроса на сервер отчетов создается новый экземпляр файла журнала.<br /><br /> По умолчанию размер журналов трассировки ограничен 32 МБ, а срок их хранения — 14 дней.|  
  
## <a name="configuration-settings-for-report-server-http-log"></a>Параметры конфигурации для журнала HTTP сервера отчетов  
 Чтобы настроить конфигурацию журнала HTTP-сервера отчетов, измените файл ReportingServicesService.exe.config с помощью программы Блокнот. Этот файл конфигурации находится в папке \Program Files\Microsoft SQL Server\MSSQL.n\Reporting Services\ReportServer\Bin.  
  
 Чтобы разрешить применение сервера HTTP, необходимо добавить запись **http:4** в раздел RStrace файла ReportingServicesService.exe.config. Все другие записи файла журнала HTTP являются необязательными. Следующий пример содержит все параметры, так что можно вставить целый раздел над разделом RStrace, а затем удалить ненужные параметры.
  
```  
   <RStrace>  
         <add name="FileName" value="ReportServerService_" />  
         <add name="FileSizeLimitMb" value="32" />  
         <add name="KeepFilesForDays" value="14" />  
         <add name="Prefix" value="tid, time" />  
         <add name="TraceListeners" value="debugwindow, file" />  
         <add name="TraceFileMode" value="unique" />  
         <add name="HttpTraceFileName" value="ReportServerService_HTTP_" />  
         <add name="HttpTraceSwitches" value="date,time,clientip,username,serverip,serverport,host,method,uristem,uriquery,protocolstatus,bytesreceived,timetaken,protocolversion,useragent,cookiereceived,cookiesent,referrer" />  
         <add name="Components" value="all:3,http:4" />  
   </RStrace>  
```  
  
## <a name="log-file-fields"></a>Поля файла журнала  
 В следующей таблице описаны поля, доступные в журнале. Список полей можно изменить. С помощью параметра конфигурации **HTTPTraceSwitches** можно указать, какие поля необходимо включить. Столбец **По умолчанию** указывает, будет ли поле включено в файл журнала автоматически, если не указано значение **HTTPTraceSwitches**.  
  
|Поле|Описание|По умолчанию|  
|-----------|-----------------|-------------|  
|HttpTraceFileName|Это значение является необязательным. Значением по умолчанию является ReportServerServiceHTTP_. Можно указать другое значение, если требуется использовать другое соглашение об именах (например, чтобы включить имя сервера, если файлы журналов сохраняются в каком-то централизованном расположении).|Да|  
|HTTPTraceSwitches|Это значение является необязательным. Если указан этот параметр, можно настроить поля, используемые в файле журнала, в формате с разделителями-запятыми.|нет|  
|Дата|Дата, когда произошло действие.|нет|  
|Time|Время, в которое произошло указанное действие.|нет|  
|ClientIp|IP-адрес клиента, получающего доступ к серверу отчетов.|Да|  
|UserName|Имя пользователя, который получил доступ к серверу отчетов.|нет|  
|ServerPort|Номер порта, используемого для соединения.|нет|  
|Узел|Содержимое заголовка узла.|нет|  
|Метод|Действие или метод SOAP, вызванный из клиентского приложения.|Да|  
|UriStem|Ресурс, к которому получен доступ.|Да|  
|UriQuery|Запрос, использованный для доступа к ресурсу.|нет|  
|ProtocolStatus|Код состояния HTTP.|Да|  
|BytesReceived|Число байт, полученных сервером.|нет|  
|TimeTaken|Время (в миллисекундах), прошедшее с момента возврата компонентом HTTP.SYS данных запроса до завершения последней отправки сервером, в которое не входит время передачи по сети.|нет|  
|ProtocolVersion|Версия протокола, используемого клиентом.|нет|  
|UserAgent|Тип браузера, используемый клиентом.|нет|  
|CookieReceived|Содержимое куки-файла, полученного сервером.|нет|  
|CookieSent|Содержимое куки-файла, отправленного сервером.|нет|  
|Referrer|Предыдущий сайт, посещенный клиентом.|нет|  
  
## <a name="see-also"></a>См. также:  
 [Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)   
 [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
