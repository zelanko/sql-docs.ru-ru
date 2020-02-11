---
title: Программа RS.exe (SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6c4bf8f67f787214d38148db40ea8122a064a42
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099828"
---
# <a name="rsexe-utility-ssrs"></a>Служебная программа RS.exe (SSRS)
  Скрипт, предоставленный во входном файле, обрабатывается служебной программой rs.exe. Используйте эту программу для автоматизации развертывания сервера отчетов и административных задач.  
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], поддерживается применение служебной программы **rs** к серверам отчетов, которые настроены для режима интеграции с SharePoint, а также к серверам, настроенным в основном режиме. В предыдущих версиях поддерживалась только работа в собственном режиме.  
  
 **В этом разделе:**  
  
-   [Расположение файла](#bkmk_filelocation)  
  
-   [Аргументы](#bkmk_arguments)  
  
-   [Разрешения](#bkmk_permissions)  
  
-   [Примеры](#bkmk_examples)  
  
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
  
##  <a name="bkmk_filelocation"></a>Расположение файла  
 **Файл RS. exe** находится в **папке \Program Files\Microsoft SQL Server\110\Tools\Binn**. Программу можно запустить из любой папки файловой системы.  
  
##  <a name="bkmk_arguments"></a>Даваемых  
 **-?**  
 Показывает синтаксис аргументов **rs** (необязательно).  
  
 `-i`*input_file*  
 (обязательный) Определяет файл rss, подлежащий выполнению. Это значение может быть как относительным, так и полным путем к файлу rss.  
  
 `-s`*ServerUrl*  
 (обязательный) Определяет имя веб-сервера и имя виртуального каталога сервера отчетов, к которым будет применен выполняемый файл. Пример URL-адреса сервера отчетов: `http://examplewebserver/reportserver`. Префикс http:// или https: // в начале имени сервера необязателен. Если префикс не указан, то сервер, на котором находится скрипт сервера отчетов, сначала пытается использовать протокол HTTPS, а в случае неудачи — протокол HTTP.  
  
 `-u`[*домен*\\] *имя пользователя*  
 (Необязательный) Определяет учетную запись пользователя, используемую для подключения к серверу отчетов. В случае отсутствия `-u` и `-p` используется текущая учетная запись пользователя Windows.  
  
 `-p`*пароль*  
 (обязательный, если задан `-u`) Определяет пароль для использования с аргументом `-u`. Это значение учитывает регистр.  
  
 `-e`  
 (Необязательный) Определяет конечную точку SOAP, с которой должен выполняться скрипт. Допустимы следующие значения.  
  
-   Mgmt2010  
  
-   Mgmt2006  
  
-   Mgmt2005  
  
-   Exec2005  
  
 Если значение не указано, то используется конечная точка Mgmt2005. Дополнительные сведения о конечных точках SOAP см. в разделе [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).  
  
 `-l`*time_out*  
 Используемых Указывает количество секунд, которое должно пройти до истечения времени ожидания соединения с сервером. Значение по умолчанию — 60 секунд. Если значение времени ожидания не определено, то используется значение по умолчанию. Значение `0` определяет бесконечное время ожидания соединения.  
  
 **-б**  
 (Необязательный) Задает пакетное выполнение команд файла скрипта. В случае ошибки любой из команд происходит откат всего пакета к прежнему состоянию. Некоторые команды не могут быть помещены в пакет и будут выполняться обычным способом. Откат вызывается только исключениями, которые возникли, но не обрабатываются скриптом. Если скрипт обрабатывает исключение и возвращается из функции `Main` без ошибок, пакет фиксируется. Если этот параметр не указан, то команды выполняются без создания пакета. Дополнительные сведения см. в статье [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).  
  
 `-v`*глобалвар*  
 (Необязательный) Определяет глобальные переменные, которые используются в скрипте. Если скрипт использует глобальные переменные, то необходимо задать этот аргумент. Задаваемое значение должно быть допустимым для глобальной переменной, определенной в файле rss. Необходимо задать одну глобальную переменную для каждого аргумента **-v**.  
  
 Аргумент `-v` задается в командной строке и используется для указания значения глобальной переменной, которая определяется в скрипте во время выполнения. Например, если скрипт содержит переменную с именем *parentFolder*, можно указать имя для соответствующей папки в командной строке:  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 Глобальные переменные создаются с указанными именами и им присваиваются заданные значения. Например, **-v a =**"`1`" **-v b =**"`2`" приводит к переменной с именем `a` со значением "`1`" и переменной **b** со значением "`2`".  
  
 Глобальные переменные доступны для любой функции в скрипте. Обратная косая черта и кавычка (**\\"**) интерпретируется как двойная кавычка. Кавычки требуются только в том случае, если строка содержит пробелы. Имена переменных должны быть допустимыми [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]для; они должны начинаться с алфавитного символа или знака подчеркивания и содержать буквы, цифры или символы подчеркивания. Зарезервированные слова не могут использоваться в качестве имен переменных. Дополнительные сведения об использовании глобальных переменных см. в разделе [Встроенные коллекции в выражениях (построитель отчетов и службы SSRS)](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **-t**  
 (Необязательный) Записывает сообщения об ошибках в журнал трассировки. Этот аргумент не принимает значения. Дополнительные сведения см. в статье [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).  
  
##  <a name="bkmk_permissions"></a> Permissions  
 Для запуска этого средства необходимо иметь разрешение на подключение к экземпляру сервера отчетов, с которым работает выполняемый скрипт. Можно выполнять скрипты для внесения изменений на локальном или удаленном компьютере. Для внесения изменений на сервере отчетов, установленном на удаленном компьютере, укажите удаленный компьютер в аргументе `-s`.  
  
##  <a name="bkmk_examples"></a> Примеры  
 В следующем примере показано, как задать файл скрипта, содержащего скрипт [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, и методы веб-службы, которые требуется выполнить.  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 Подробный пример см. в разделе [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Дополнительные примеры см. в разделе [Запуск файла скрипта для служб Reporting Services](run-a-reporting-services-script-file.md)  
  
## <a name="remarks"></a>Remarks  
 Можно определять скрипты, устанавливать системные свойства, публиковать отчеты и так далее. Создаваемые скрипты могут включать любые методы API-интерфейса служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения о доступных методах и свойствах см. в разделе [Report Server Web Service](../report-server-web-service/report-server-web-service.md).  
  
 Скрипт должен быть написан на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET и храниться в текстовом файле в кодировке Юникод или UTF-8 с расширением RSS. Отладить скрипт с помощью программы **rs** невозможно. Чтобы выполнить отладку скрипта, выполните код [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]в.  
  
> [!TIP]  
>  Подробный пример см. в разделе [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
## <a name="see-also"></a>См. также:  
 [Запуск файла скрипта Reporting Services](run-a-reporting-services-script-file.md)   
 [Создание скриптов для задач развертывания и администрирования](script-deployment-and-administrative-tasks.md)   
 [Создание скрипта с помощью служебной программы RS. exe и веб-службы](script-with-the-rs-exe-utility-and-the-web-service.md)   
 [Программы командной строки сервера отчетов &#40;службы SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)  
  
  
