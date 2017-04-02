---
title: "Командлет Merge-Partition | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 15c7b069-897d-4bc8-a808-59cbeeabe4d8
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Командлет Merge-Partition
  Выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.  
  
## Синтаксис  
 `Merge-ASDatabase [-Name] <string> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
 `Merge-ASDatabase -TargetPartition <Microsoft.AnalysisServices.Partition> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Командлет Merge-Partition выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции. Можно выполнять слияние секций только в том случае, если они удовлетворяют всем перечисленным далее условиям.  
  
-   Секции находятся в одной и той же группе мер.  
  
-   Секции расположены на одном и том же компьютере.  
  
-   Секции используют один и тот же режим хранения (MOLAP, HOLAP и ROLAP для многомерных баз данных).  
  
## Параметры  
  
### -Name \<строка>  
 Указывает целевую секцию, в которой будут объединены данные исходных секций. Эта секция должна уже существовать.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -SourcePartition \<строка>  
 Указывает исходную секцию, данные которой будут объединены в целевой секции. Вы можете создать список с разделителями-запятыми тех секций, которые требуется объединить. Для сохранения списка используйте переменную. Например, $Sources=”Sales_2008”, “Sales_2009”, “Sales_2010”.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Database \<строка>  
 Указывает базу данных, в которой находятся секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Cube \<строка>  
 Указывает куб, к которому относятся секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -MeasureGroup \<строка>  
 Указывает группу мер, к которой принадлежит секция.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Server \<строка>  
 Указывает экземпляр служб Analysis Services, к которому подключится командлет и где он будет выполняться. Если имя сервера не указано, произойдет подключение к серверу localhost. Для экземпляров по умолчанию достаточно указать имя сервера. Для именованных экземпляров используйте формат имя_сервера\имя_экземпляра. Для HTTP-соединений используйте формат http[s]://server[:port]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|localhost|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Credential \<учетные данные ПК>  
 Этот параметр используется для передачи имени пользователя и пароля, если используется HTTP-соединение с экземпляром служб Analysis Service, настроенным на доступ по протоколу HTTP. Дополнительные сведения о HTTP-соединениях см. в разделе [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md) и [Создание скриптов PowerShell в службах Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md).  
  
 Если этот параметр задан, указанные имя пользователя и пароль будут использоваться для подключения к заданному экземпляру сервера анализа данных. Если учетные данные не указаны, для пользователя, запустившего это средство, будет использоваться учетная запись Windows по умолчанию.  
  
 Для использования этого параметра необходимо сначала создать объект PSCredential с помощью командлета Get-Credential, чтобы указать имя пользователя и пароль (например, `$Cred=Get-Credential “adventure-works\bobh”`. этот объект можно затем передать по конвейеру в параметр –Credential `(-Credential:$Cred`.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|True (ByValue)|  
|Принимать символы-шаблоны?|false|  
  
### -TargetPartition \<Microsoft.AnalysisServices.Partition>  
 Указывает целевую секцию, в которой будут объединены исходные секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|System.String|  
|Выходные данные|Нет|  
  
## Пример 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> $Source=”Total_Orders_2001”, “Total_Orders_2002”, “Total_Orders_2003”` `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> Merge-Partition –Name “Total_Orders_2004” –SourcePartitions:$Source –database “AWTEST” –cube “Adventure Works” –MeasureGroup “Sales Orders”`  
  
 Эта команда выполняет слияние данных за 2001, 2002 и 2003 годы в секцию за 2004 год, после чего удаляет секции за предыдущие годы.  
  
## См. также  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Управление табличными моделями с помощью PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  