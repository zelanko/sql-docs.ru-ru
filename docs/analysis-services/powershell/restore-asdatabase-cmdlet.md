---
title: "Командлет RESTORE-ASDatabase | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ab7a2d0-679c-40e6-b9b9-042184b2dfc9
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 86894e5f3c0d438a5a97c45e3927e3996ee6a6ab
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="restore-asdatabase-cmdlet"></a>Командлет Restore-ASDatabase
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Восстанавливает файл резервной копии (ABF) многомерной или табличной базы данных экземпляра служб Analysis Services.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `Restore-ASDatabase [-RestoreFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] Locations <Microsoft.AnalysisServices.RestoreLocation[]>] [-Security <Microsoft.AnalysisServices.RestoreSecurity>] [-Password <System.SecureString>] [-StorageLocation <System.string>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Дает возможность системному администратору служб Analysis Services восстанавливать многомерную или табличную базу данных из файла резервной копии (ABF-файла) на экземпляре локального или удаленного сервера. Если восстанавливаемый файл был зашифрован, используйте параметр –FilePassword, чтобы указать пароль, который будет использоваться для расшифровки файла.  
  
 Этот командлет поддерживает параметр –Credential, который можно использовать, если экземпляр служб Analysis Services настроен для доступа по протоколу HTTP. Параметр –Credential принимает объект PSCredential, который содержит идентификатор пользователя Windows. Службы IIS будут олицетворять этого пользователя при подключении к службам Analysis Services. Чтобы восстановить файл, необходимо обладать разрешениями системного администратора на этом экземпляре служб Analysis Services.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-restorefile-string"></a>-RestoreFile \<строка >  
 Задает путь и имя восстанавливаемого файла. Если указать только имя файла без пути, будет использоваться хранилище резервных копий по умолчанию.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-name-string"></a>-Имя \<строка >  
 Указывает базу данных служб Analysis Services, резервная копия которой восстанавливается.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-allowoverwrite-switchparameter"></a>-AllowOverwrite \<SwitchParameter >  
 Перезаписывает базу данных с тем же именем и в том же расположении.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-locations-microsoftanalysisservicesrestorelocation"></a>-Расположения \<Microsoft.AnalysisServices.RestoreLocation [] >  
 Указывает расположение удаленных восстанавливаемых секций.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-security-microsoftanalysisservicesrestoresecurity"></a>-Security \<Microsoft.AnalysisServices.RestoreSecurity >  
 Представляет параметры безопасности, используемые для операции восстановления. Допустимы значения: CopyAll, SkipMembership, IgnoreSecurity. CopyAll восстанавливает роли и членство в них. SkipMembership восстанавливает только роль. IgnoreSecurity восстанавливает базу данных без ролей.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-password-securestring"></a>-Пароль \<SecureString >  
 Указывает пароль, используемый для восстановления зашифрованного файла резервной копии. Необходимо указать пароль, который первоначально использовался для шифрования файла.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-storagelocation-string"></a>-StorageLocation \<строка >  
 Указывает место хранения базы данных. Это расположение файлов базы данных в файловой системе. Установите этот параметр, если используется не расположение по умолчанию, которое соответствует папке резервных копий на целевом экземпляре.  
  
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
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|System.String<br /><br /> В командлет можно передавать по конвейеру строковые значения.|  
|Выходные данные|Нет.|  
  
## <a name="example-1"></a>Пример 1  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase awtest.abf testawrestoredb –security:CopyAll  
```  
  
 Эта команда восстанавливает файл резервной копии служб Analysis Services (awtest.abf) из локальной папки резервных копий на локальный экземпляр служб Analysis Services по умолчанию. Имя базы данных не обязательно должно существовать; в этом случае имя базы данных задается в процессе операции восстановления. При указании ключа –Security:CopyAll в новую (восстанавливаемую) базу данных из резервной копии базы данных будут добавлены роли и членство в ролях.  
  
## <a name="example-2"></a>Пример 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile testdb.abf –name AWTEST2 –password:$pwd  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Строки 1 и 2 используются для запроса пароля, который был использован для шифрования файла.  
  
 Строка 3 используется для восстановления зашифрованного файла резервной копии (testdb.abf) из локальной папки резервных копий экземпляра служб Analysis Services по умолчанию.  
  
 Строки 4 и 5 удаляют пароль.  
  
## <a name="example-3-remote-scenario"></a>Пример 3 (удаленный сценарий)  
 В этом примере показано, как восстановить локальный файл резервной копии из общей папки на удаленном экземпляре служб Analysis Services. Здесь файл резервной копии восстанавливается в виде базы данных с именем **internetsales** на экземпляре служб Analysis Services по умолчанию на компьютере с именем **ssas-aw-srv01**.  
  
 Файл резервной копии находится на общем сетевом ресурсе с общим доступом на чтение. Удаленный экземпляр служб Analysis Services должен иметь разрешение на чтение файла. Расположением файла должна быть сетевая папка (без дисков).  
  
 Обратите внимание, что этот пример не зависит от поставщика SQLAS. Командлет можно запустить как автономную команду.  
  
```  
PS SQLSERVER:\> restore-asdatabase -restorefile "\\FileServer01\DBFiles\InternetSalesTabular.abf" -name "internetsales  
" -server "SSAS-AW-SRV01"  
```  
  
## <a name="example-4"></a>Пример 4  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile “\\myremoteserver\backups\testdb.abf” –name Contoso_Retail –server myremoteserver –storagelocation “\\myremoteserver\restoreDBFiles”  
```  
  
 Эта команда восстанавливает зашифрованный файл резервной копии служб Analysis Services (testdb.abf) из удаленной папки резервных копий на удаленный экземпляр служб Analysis Services по умолчанию. Параметр —StorageLocation используется для помещения файлов базы данных в расположение, отличное от расположения по умолчанию, в данном случае — в общий файловый ресурс restoreDBfiles.  
  
