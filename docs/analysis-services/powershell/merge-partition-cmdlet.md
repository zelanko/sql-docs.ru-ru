---
title: Командлет Merge-Partition | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f78b946367c6bff01ab233cf5f4382ee3b9057e0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029085"
---
# <a name="merge-partition-cmdlet"></a>Командлет Merge-Partition
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `Merge-ASDatabase [-Name] <string> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
 `Merge-ASDatabase -TargetPartition <Microsoft.AnalysisServices.Partition> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Описание  
 Командлет Merge-Partition выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции. Можно выполнять слияние секций только в том случае, если они удовлетворяют всем перечисленным далее условиям.  
  
-   Секции находятся в одной и той же группе мер.  
  
-   Секции расположены на одном и том же компьютере.  
  
-   Секции используют один и тот же режим хранения (MOLAP, HOLAP и ROLAP для многомерных баз данных).  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-name-string"></a>-Имя \<строка >  
 Указывает целевую секцию, в которой будут объединены данные исходных секций. Эта секция должна уже существовать.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-sourcepartition-string"></a>-SourcePartition \<строка >  
 Указывает исходную секцию, данные которой будут объединены в целевой секции. Вы можете создать список с разделителями-запятыми тех секций, которые требуется объединить. Для сохранения списка используйте переменную. Например, $Sources=”Sales_2008”, “Sales_2009”, “Sales_2010”.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-database-string"></a>-Базы данных \<строка >  
 Указывает базу данных, в которой находятся секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-cube-string"></a>-Cube \<строка >  
 Указывает куб, к которому относятся секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-measuregroup-string"></a>-MeasureGroup \<строка >  
 Указывает группу мер, к которой принадлежит секция.  
  
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
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Этот параметр используется для передачи имени пользователя и пароля, если используется HTTP-соединение с экземпляром служб Analysis Service, настроенным на доступ по протоколу HTTP. Дополнительные сведения см. в разделе [Настройка доступа по протоколу HTTP к службам Analysis Services в службах Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md) для HTTP-соединений.  
  
 Если этот параметр задан, указанные имя пользователя и пароль будут использоваться для подключения к заданному экземпляру сервера анализа данных. Если учетные данные не указаны, для пользователя, запустившего это средство, будет использоваться учетная запись Windows по умолчанию.  
  
 Для использования этого параметра необходимо сначала создать объект PSCredential с помощью командлета Get-Credential, чтобы указать имя пользователя и пароль (например, `$Cred=Get-Credential “adventure-works\bobh”`. этот объект можно затем передать по конвейеру в параметр –Credential `(-Credential:$Cred`.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|True (ByValue)|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-targetpartition-microsoftanalysisservicespartition"></a>-TargetPartition \<Microsoft.AnalysisServices.Partition >  
 Указывает целевую секцию, в которой будут объединены исходные секции.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|System.String|  
|Выходные данные|Нет|  
  
## <a name="example-1"></a>Пример 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> $Source=”Total_Orders_2001”, “Total_Orders_2002”, “Total_Orders_2003”` `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> Merge-Partition –Name “Total_Orders_2004” –SourcePartitions:$Source –database “AWTEST” –cube “Adventure Works” –MeasureGroup “Sales Orders”`  
  
 Эта команда выполняет слияние данных за 2001, 2002 и 2003 годы в секцию за 2004 год, после чего удаляет секции за предыдущие годы.  
  

  
