---
title: "Командлет Invoke-ASCmd | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2896b74a-3911-4b3f-89ab-bb375bdb34d8
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 366263980ae7ad9d5a792e6525888080a38ebbf6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-ascmd-cmdlet"></a>Командлет Invoke-ASCmd

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Позволяет администратору базы данных выполнить сценарий XMLA, многомерные выражения (MDX), инструкции расширений интеллектуального анализа данных (DMX) или сценарий TMSL.  
  
 Язык TMSL поддерживается только в табличном режиме сервера в экземпляре служб Analysis Services SQL Server 2016.  
  
 Если вы хотите создать базы данных или другие объекты, то используете именно этот командлет с входным файлом сценария.  
  
## <a name="syntax"></a>Синтаксис  
 `Invoke-ASCmd –Query <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
 `Invoke-ASCmd –InputFile <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Командлет ASCmd может выполнять запросы или скрипты, содержащиеся во входных файлах.  
  
 Поддерживаются следующие команды для XMLA: Alter, Backup, Batch, BeginTransaction, Cancel, ClearCache, CommitTransaction, Create, Delete, DesignAggregations, Drop, Insert, Lock, MergePartitions, NotifyTableChange, Process, Restore, RollbackTransaction, SetPasswordEncryptionKey, Statement (используется для выполнения запросов многомерных выражений и инструкций расширений интеллектуального анализа данных), Subscribe, Synchronize, Unlock, Update, UpdateCells.  
  
 Для TMSL: Alter, Create, Delete, MergePartitions, Process, Update.  
  
 Этот командлет поддерживает параметр –Credential, который можно использовать, если экземпляр служб Analysis Services настроен для доступа по протоколу HTTP. Параметр –Credential принимает объект PSCredential, который содержит идентификатор пользователя Windows. Службы IIS будут олицетворять этого пользователя при подключении к службам Analysis Services. Чтобы запустить скрипт, необходимо обладать разрешениями системного администратора на этом экземпляре служб Analysis Services.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-query-string"></a>-Query \<строка >  
 Указывает, что фактический скрипт, запрос или инструкция задается непосредственно в командной строке, а не в файле. Также запрос можно указать в качестве входа конвейера. При использовании командлета **Invoke-AsCmd** необходимо указать либо значение **–InputFile** , либо значение **–Query**.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|True (ByValue)|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-inputfile-string"></a>-InputFile \<строка >  
 Идентифицирует файл, содержащий сценарий XMLA, запрос многомерных выражений, инструкцию расширения интеллектуального анализа данных или сценарий TMSL (в формате JSON). При использовании командлета **Invoke-AsCmd** необходимо указать либо значение **–InputFile** , либо значение **–Query**.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-server-string"></a>-Server \<строка >  
 Указывает экземпляр служб Analysis Services, к которому подключится командлет и где он будет выполняться. Если имя сервера не указано, произойдет подключение к серверу localhost. Для экземпляров по умолчанию достаточно указать имя сервера. Для именованных экземпляров используйте формат имя_сервера\имя_экземпляра. Для HTTP-соединений используйте формат http[s]://server[:port]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|localhost|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-database-string"></a>-Базы данных \<строка >  
 Определяет базу данных, в которой выполняются запросы MDX или инструкции DMX. Параметр базы данных не учитывается, если командлет выполняет скрипт XML для аналитики, так как скрипт XML для аналитики содержит внедренное имя базы данных.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Указывает объект PSCredential, который содержит имя пользователя и пароль Windows. Укажите этот параметр, только если экземпляр служб Analysis Services настроен для доступа HTTP с использованием обычной проверки подлинности. Для соединений в собственном режиме, в которых используются интегрированные функции безопасности, этот параметр не учитываются.  
  
 Если этот параметр указан, учетные данные, которые он содержит, добавляются в строку подключения. Службы IIS будут олицетворять этого пользователя при соединении со службами Analysis Services. Если учетные данные не будут указаны, будут использованы учетные данные по умолчанию для пользователя, который запускает это средство.  
  
 Для использования этого параметра необходимо сначала создать объект PSCredential с помощью командлета Get-Credential, чтобы указать имя пользователя и пароль (например, `$Cred=Get-Credential “adventure-works\admin”`. этот объект можно затем передать по конвейеру в параметр –Credential `(-Credential:$Cred`.  
  
   Дополнительные сведения о HTTP-доступе см. в разделе [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|True (ByValue)|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-connectiontimeout-int"></a>-ConnectionTimeout \<int >  
 Задает количество секунд до истечения времени ожидания соединения с экземпляром служб Analysis Services. Значение времени ожидания должно быть целым числом от 0 до 65 534. Если указано значение 0, попытки соединения не прекращаются.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|30|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-querytimeout-int"></a>-QueryTimeout \<int >  
 Задает время ожидания запросов (в секундах). Если значение времени ожидания не указано, срок выполнения запросов неограничен. Время ожидания должно быть целым числом от 1 до 65 535.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|30|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-variable-string"></a>-Переменной \<string [] >  
 Задаются дополнительные переменные скрипта. Каждая переменная является парой «имя-значение». Если в значении содержатся пробелы или управляющие символы, оно должно заключаться в двойные кавычки. Для указания нескольких переменных и их значений используйте массив PowerShell.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-tracefile-string"></a>-TraceFile \<строка >  
 Определяет файл, в который поступают события трассировки служб Analysis Services при выполнении скрипта XML для аналитики, запроса многомерных выражений или инструкции расширений интеллектуального анализа данных. Если файл уже существует, он будет автоматически перезаписан (кроме файлов трассировки, созданных с параметрами -TraceLevel:Duration и –TraceLevel:DurationResult). Имена файлов, содержащие пробелы, должны быть заключены в кавычки (""). Если указано недопустимое имя файла, выдается сообщение об ошибке.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-tracefileformat-string"></a>-TraceFileFormat \<строка >  
 Устанавливает формат файла для параметра –TraceFile (если этот параметр указан). Доступны следующие значения: text и csv. Значением по умолчанию является «csv».  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|csv|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-tracefiledelimiter-string"></a>-TraceFileDelimiter \<строка >  
 Указывает, какой символ будет использоваться в качестве разделителя в файле трассировки, если выбран формат файла трассировки CSV. Разделителем по умолчанию является символ | (вертикальная черта).  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-tracetimeout-int"></a>-TraceTimeout \<int >  
 Задает количество секунд, в течение которых ядро служб Analysis Services ожидает, прежде чем завершить трассировку (если указан параметр –TraceFile). Предполагается, что трассировка заканчивается, если в течение заданного периода времени не записываются никакие сообщения трассировки. По умолчанию период равен 5 секундам.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|5|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-tracelevel-traceleveloption"></a>-TraceLevel \<TraceLevelOption >  
 Задает тип данных, которые собираются и записываются в файл трассировки. Возможны следующие значения: High, Medium, Low, Duration, DurationResult.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|Высокий|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|PSObject|  
|Выходные данные|Строковые значения|  
  
## <a name="example-1-xmla-input-file"></a>Пример 1 (с входным файлом XMLA)  
  
```  
Invoke-ASCmd –InputFile:"C:\MyFolder\DiscoverConnections.xmla"  
```  
  
 Эта команда выполняет скрипт XML для аналитики, возвращающий список активных соединений с сервером. Файл DiscoverConnections.xmla содержит следующий скрипт XML для аналитики:  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
<RequestType>DISCOVER_CONNECTIONS</RequestType>  
<Restrictions />  
   <Properties>  
      <PropertyList>  
         <Content>Data</Content>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="example-2-tmsl-input-file"></a>Пример 2 (с входным файлом TMSL)  
 Этот пример идентичен первому, только теперь используется сценарий TMSL (JSON) и требуется табличный экземпляр SQL Server 2016. Вы можете создать сценарий TMSL в SQL Server Management Studio.  
  
 Если используется несколько экземпляров и табличным является именованный экземпляр, не забудьте задать имя сервера.  
  
```  
Invoke-ASCmd –InputFile "C:\folder-name\T1200-NewDB.json" -Server "server-name\instance-name"  
```  
  
## <a name="example-3-query"></a>Пример 3 (запрос)  
  
```  
Invoke-ASCmd -Database:"Adventure Works DW" -Query:"<Discover xmlns='urn:schemas-microsoft-com:xml analysis'><RequestType>DISCOVER_DATASOURCES</RequestType><Restrictions></Restrictions><Properties></Properties></Discover>"  
```  
  
 Запрос Discover в XML для аналитики возвращает доступные источники данных для сервера анализа данных, а также необходимые для подключения к ним сведения. Результаты возвращаются в формате XML. Чтобы упростить чтение, выходные данные можно перенаправить в XML-файл (например, добавив в команду `| Out-file C:\Results\XMLAQueryOutput.xml` ) и просмотреть результаты в браузере или другом приложении, поддерживающем структурированный код XML.  
  
  
  
