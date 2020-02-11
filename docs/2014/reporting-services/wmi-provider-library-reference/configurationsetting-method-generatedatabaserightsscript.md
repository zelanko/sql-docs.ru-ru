---
title: Метод GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 575eab878e0ef9b4357c09a0a3deedf143c237b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098474"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a>Метод GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting)
  Создает скрипт SQL, с помощью которого пользователям могут предоставляться права доступа к базе данных сервера отчетов и другим базам данных, необходимым для работы сервера отчетов. Ожидается, что участник соединится с базой данных сервера отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнит скрипт.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Имен*  
 Имя пользователя или идентификатор безопасности Windows пользователя, которому скрипт предоставляет права.  
  
 *имя_базы_данных*  
 Имя базы данных, доступ к которой скрипт предоставит пользователю.  
  
 *Удаленный*  
 Логическое значение. Показывает, является ли база данных удаленной по отношению к серверу отчетов.  
  
 *Параметр IsWindowsUser*  
 Логическое значение, которое показывает тип пользователя для указанного имени пользователя: Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 *Скрипт*  
 [out] Строка, которая содержит созданный скрипт [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 *СОСТАВ*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Если параметр *DatabaseName* пуст, *IsRemote* пропускается и значение файла конфигурации сервера отчетов используется в качестве имени базы данных.  
  
 Если *параметр IsWindowsUser* имеет значение `true`, то *имя пользователя* должно быть в формате \<домен>\\<имя\>пользователя.  
  
 Если ** для `true`параметр IsWindowsUser задано значение, созданный скрипт предоставляет пользователю права на вход в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]систему, задание базы данных сервера отчетов в качестве базы данных по умолчанию и предоставляет роль **RSExec** в базе данных сервера отчетов, временной базе данных сервера отчетов, базе данных master и системной базе данных msdb.  
  
 Если ** для `true`параметр IsWindowsUser задано значение, метод принимает в качестве входных данных стандартные идентификаторы безопасности Windows. Если предоставлен стандартный идентификатор безопасности Windows или имя учетной записи службы, то они переводятся в строку имени пользователя. Если база данных локальная, то учетная запись переводится в соответствии с представлением текущего языкового стандарта учетной записи. Если база данных удаленная, то учетная запись представляется как учетная запись компьютера.  
  
 В приведенной ниже таблице показаны переведенные учетные записи и их удаленное представление.  
  
|Переведенная учетная запись/идентификатор безопасности|Общее имя|Удаленное имя|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|Локальная система|
  \<Домен>\\<имя_компьютера\>$|  
|.\LocalSystem|Локальная система|
  \<Домен>\\<имя_компьютера\>$|  
|ComputerName\LocalSystem|Локальная система|
  \<Домен>\\<имя_компьютера\>$|  
|локальная система;|Локальная система|
  \<Домен>\\<имя_компьютера\>$|  
|(S-1-5-20)|Сетевая служба.|
  \<Домен>\\<имя_компьютера\>$|  
|NT AUTHORITY\NetworkService|Сетевая служба.|
  \<Домен>\\<имя_компьютера\>$|  
|(S-1-5-19)|Локальная служба.|Ошибка — см. ниже.|  
|NT AUTHORITY\LocalService|Локальная служба.|Ошибка — см. ниже.|  
  
 Если в [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]используется встроенная учетная запись, а база данных сервера отчетов удаленная, то возвращается сообщение об ошибке.  
  
 Если указана встроенная учетная запись `LocalService` и база данных сервера отчетов удаленная, то возвращается сообщение об ошибке.  
  
 Если параметр *IsWindowsUser* имеет значение true, а значение параметра *UserName* требует перевода, то поставщик WMI определяет, на каком компьютере находится база данных сервера отчетов: на этом же или на удаленном. Чтобы определить, что установка локальная, поставщик WMI проверяет свойство DatabaseServerName на значения из приведенного ниже списка. Если одно из значений совпадает, то база данных локальная. В противном случае она является удаленной. При сравнении регистр не учитывается.  
  
|Значение параметра DatabaseServerName|Пример|  
|---------------------------------|-------------|  
|"."||  
|"(local)"||  
|"LOCAL"||  
|localhost||  
|\<MachineName>|testlab14|  
|
  \<Полное_доменное_имя_компьютера>|example.redmond.microsoft.com|  
|\<IPAddress>|180.012.345,678|  
  
 Если ** для `true`параметр IsWindowsUser задано значение, поставщик WMI вызывает LookupAccountName, чтобы получить идентификатор безопасности для учетной записи, а затем вызывает LookupAccountSID, чтобы получить имя, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помещаемое в скрипт. Это гарантирует, что имя учетной записи успешно пройдет проверку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если ** для `false`параметр IsWindowsUser задано значение, то созданный скрипт предоставляет роль **RSExec** в базе данных сервера отчетов, временной базе данных сервера отчетов и базе данных msdb.  
  
 Если *параметр IsWindowsUser* имеет значение `false`, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для успешного выполнения скрипта SQL Server пользователь должен уже существовать в.  
  
 Если для сервера отчетов не задана база данных сервера отчетов, то при вызове метода GrantRightsToDatabaseUser возвращается ошибка.  
  
 Созданный скрипт поддерживает [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
