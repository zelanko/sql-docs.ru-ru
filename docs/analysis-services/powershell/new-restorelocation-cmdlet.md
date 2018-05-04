---
title: Командлет New-RestoreLocation | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43d0ad50544be56628b9aaa48494bb84351eb0ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-restorelocation-cmdlet"></a>Командлет New-RestoreLocation
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Указывает сведения, используемые для восстановления базы данных.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `New-RestoreLocation [-File <String>] [-DataSourceId <String>] [-ConnectionString <String>] [-DataSourceType <RestoreDataSourceType>] [-Folders <RestoreFolder[]>] [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreLocation [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Общие параметры, такие как –Verbose, -Debug, сообщения управления ошибками и предупреждениями, -Whatif и –Confir документированы в справке по Windows PowerShell. Дополнительные сведения см. в разделе [Об общих параметрах](http://technet.microsoft.com/library/dd315352.aspx).  
  
## <a name="description"></a>Описание  
 Командлет New-RestoreLocation содержит сведения, используемые для восстановления базы данных, в том числе строку подключения с сервером и базой данных, свойства источника данных, файлы и папки, связанные с восстанавливаемой базой данных.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-file-string"></a>-Файла \<строка >  
 Указывает имя файла резервной копии, из которого производится восстановление.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-datasourceid-string"></a>-DataSourceId \<строка >  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-connectionstring-string"></a>-ConnectionString \<строка >  
 Указывает строку подключения с удаленным экземпляром служб Analysis Services.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-datasourcetype-asrestoredatasourcetype"></a>-DataSourceType \<AS. RestoreDataSourceType >  
 Указывает, является ли источник данных удаленным или локальным (исходя из расположения секции).  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-folders-asrestorefolder"></a>-Папки \<AS. RestoreFolder >  
 Указывает папки секций на локальном или удаленном экземпляре.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-astemplate-switchparameter"></a>-AsTemplate \<SwitchParameter >  
 Указывает, следует ли создать объект в памяти и возвратить его.  
  
|||  
|-|-|  
|Обязательно?|false|  
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
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет|  
|Выходные данные|Нет|  
  
## <a name="examples"></a>Примеры  
  
  
