---
title: "Служебная программа RS.exe (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
caps.latest.revision: 56
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 70f9afea9e9fe495c66ac98ea8ec4f3e9b1e3a6d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="rsexe-utility-ssrs"></a>Служебная программа RS.exe (SSRS)
  Скрипт, предоставленный во входном файле, обрабатывается служебной программой rs.exe. Используйте эту программу для автоматизации развертывания сервера отчетов и административных задач.  
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], поддерживается применение служебной программы **rs** к серверам отчетов, которые настроены для режима интеграции с SharePoint, а также к серверам, настроенным в основном режиме. В предыдущих версиях поддерживалась только работа в собственном режиме.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="bkmk_filelocation"></a> Размещение файла  
 Программа**rs.exe** находится в папке **\Program Files\Microsoft SQL Server\110\Tools\Binn**. Программу можно запустить из любой папки файловой системы.  
  
##  <a name="bkmk_arguments"></a> Аргументы  
 **-?**  
 Показывает синтаксис аргументов **rs** (необязательно).  
  
 **-i** *input_file*  
 (обязательный) Определяет файл rss, подлежащий выполнению. Это значение может быть как относительным, так и полным путем к файлу rss.  
  
 **-s** *serverURL*  
 (обязательный) Определяет имя веб-сервера и имя виртуального каталога сервера отчетов, к которым будет применен выполняемый файл. Пример URL-адреса сервера отчетов: `http://examplewebserver/reportserver`. Префикс http:// или https: // в начале имени сервера необязателен. Если префикс не указан, то сервер, на котором находится скрипт сервера отчетов, сначала пытается использовать протокол HTTPS, а в случае неудачи — протокол HTTP.  
  
 **-u** [*домен*\\]*имя_пользователя*  
 (Необязательный) Определяет учетную запись пользователя, используемую для подключения к серверу отчетов. В случае отсутствия **-u** и **-p** используется текущая учетная запись пользователя Windows.  
  
 **-p** *password*  
 (Обязательный, если задан **-u** .) Определяет пароль для использования с аргументом **-u** . Это значение учитывает регистр.  
  
 **-e**  
 (Необязательный) Определяет конечную точку SOAP, с которой должен выполняться скрипт. Допустимы следующие значения.  
  
-   Mgmt2010  
  
-   Mgmt2006  
  
-   Mgmt2005  
  
-   Exec2005  
  
 Если значение не указано, то используется конечная точка Mgmt2005. Дополнительные сведения о конечных точках SOAP см. в разделе [Report Server Web Service Endpoints](../../reporting-services/report-server-web-service/methods/report-server-web-service-endpoints.md).  
  
 **-l** *time_out*  
 (Необязательный) Определяет количество секунд, которые должны пройти до истечения времени ожидания соединения с сервером. Значение по умолчанию — 60 секунд. Если значение времени ожидания не определено, то используется значение по умолчанию. Значение **0** определяет бесконечное время ожидания соединения.  
  
 **-b**  
 (Необязательный) Задает пакетное выполнение команд файла скрипта. В случае ошибки любой из команд происходит откат всего пакета к прежнему состоянию. Некоторые команды не могут быть помещены в пакет и будут выполняться обычным способом. Откат вызывается только исключениями, которые возникли, но не обрабатываются скриптом. Если скрипт обрабатывает исключение и возвращается из функции **Main**без ошибок, пакет фиксируется. Если этот параметр не указан, то команды выполняются без создания пакета. Дополнительные сведения см. в статье [Batching Methods](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md).  
  
 **-v** *globalvar*  
 (Необязательный) Определяет глобальные переменные, которые используются в скрипте. Если скрипт использует глобальные переменные, то необходимо задать этот аргумент. Задаваемое значение должно быть допустимым для глобальной переменной, определенной в файле rss. Необходимо задать одну глобальную переменную для каждого аргумента **–v** .  
  
 Аргумент **–v** задается в командной строке и используется для указания значения глобальной переменной, которая определяется в скрипте во время выполнения. Например, если скрипт содержит переменную с именем *parentFolder*, можно указать имя для соответствующей папки в командной строке:  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 Глобальные переменные создаются с указанными именами и им присваиваются заданные значения. Например, применение **-v a=**"**1**" **-v b=**"**2**" приводит к получению переменной с именем **a** и значением "**1**", а также переменной **b** со значением "**2**".  
  
 Глобальные переменные доступны для любой функции в скрипте. Обратная косая черта и кавычка (**\\"**) интерпретируются как двойная кавычка. Кавычки требуются только в том случае, если строка содержит пробелы. Имена переменных должны быть допустимыми для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; они должны начинаться с буквы или с символа подчеркивания и содержать буквы, цифры или символы подчеркивания. Зарезервированные слова не могут использоваться в качестве имен переменных. Дополнительные сведения об использовании глобальных переменных см. в разделе [Встроенные коллекции в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **-t**  
 (Необязательный) Записывает сообщения об ошибках в журнал трассировки. Этот аргумент не принимает значения. Дополнительные сведения см. в статье [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
##  <a name="bkmk_permissions"></a> Permissions  
 Для запуска этого средства необходимо иметь разрешение на подключение к экземпляру сервера отчетов, с которым работает выполняемый скрипт. Можно выполнять скрипты для внесения изменений на локальном или удаленном компьютере. Для внесения изменений на сервере отчетов, установленном на удаленном компьютере, укажите удаленный компьютер в аргументе **-s** .  
  
##  <a name="bkmk_examples"></a> Примеры  
 В следующем примере показано, как задать файл скрипта, содержащего скрипт [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, и методы веб-службы, которые требуется выполнить.  
  
```  
rs –i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 Подробный пример см. в разделе [Образец скрипта программы rs.exe служб Reporting Services для копирования содержимого между серверами отчетов](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Дополнительные примеры см. в разделе [Запуск файла скрипта для служб Reporting Services](../../reporting-services/tools/run-a-reporting-services-script-file.md)  
  
## <a name="remarks"></a>Замечания  
 Можно определять скрипты, устанавливать системные свойства, публиковать отчеты и так далее. Создаваемые скрипты могут включать любые методы API-интерфейса служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения о доступных методах и свойствах см. в разделе [Report Server Web Service](../../reporting-services/report-server-web-service/report-server-web-service.md).  
  
 Скрипт должен быть написан на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET и храниться в текстовом файле в кодировке Юникод или UTF-8 с расширением RSS. Отладить скрипт с помощью программы **rs** невозможно. Для отладки скрипта выполните код в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!TIP]  
>  Подробный пример см. в разделе [Образец скрипта программы rs.exe служб Reporting Services для копирования содержимого между серверами отчетов](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
## <a name="see-also"></a>См. также:  
- [Запустите файл скрипта служб Reporting Services](../../reporting-services/tools/run-a-reporting-services-script-file.md)   
- [Скрипт развертывания и административных задач](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
- [Сценарий с служебную программу rs.exe и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)   
- [Программы командной строки сервера отчетов &#40; Службы SSRS &#41;](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md)  
  
  
