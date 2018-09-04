---
title: Метод ConfigurationSetting Method — GenerateDatabaseCreationScript | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 205f75710ab64fd1c93a5f82fe7a1595189ae917
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43268426"
---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>Метод ConfigurationSetting — GenerateDatabaseCreationScript
  Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Databasename*  
 Строка, которая содержит имя создаваемой базы данных сервера отчетов.  
  
 *Код языка*  
 Значение, используемое для локализованных имен ролей.  
  
 *IsSharePointMode*  
 Указывает, следует ли создать базу данных в собственном режиме или в режиме SharePoint.  
  
> [!IMPORTANT]  
>  Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], метод *IsSharePointMode*=**True** не поддерживается, поскольку в режиме SharePoint службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] являются совместно используемой службой SharePoint и не управляются средствами поставщика WMI. Этот параметр должен всегда быть установлен в значение **False**.  
  
 *Скрипт*  
 [out] Строка, содержащая сформированный скрипт SQL.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Этот метод формирует скрипт SQL, создающий базы данных сервера отчетов для версии сервера отчетов, подключенного в настоящее время.  
  
 Значение, переданное в параметре *DatabaseName* , должно соответствовать контексту именования в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 При создании скрипта этот метод не проверяет существование базы данных.  
  
 Этот метод не проверяет при создании скрипта наличие базы данных сервера отчетов.  
  
 Созданный скрипт поддерживает [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
