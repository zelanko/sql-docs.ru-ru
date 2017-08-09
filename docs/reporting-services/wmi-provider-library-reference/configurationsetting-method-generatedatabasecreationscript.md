---
title: "Метод ConfigurationSetting - GenerateDatabaseCreationScript | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6203ad120046f77ab68364f04bd93c56f9bd8cd3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>Метод ConfigurationSetting - GenerateDatabaseCreationScript
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
  
## <a name="remarks"></a>Замечания  
 Этот метод формирует скрипт SQL, создающий базы данных сервера отчетов для версии сервера отчетов, подключенного в настоящее время.  
  
 Значение, переданное в параметре *DatabaseName* , должно соответствовать контексту именования в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 При создании скрипта этот метод не проверяет существование базы данных.  
  
 Этот метод не проверяет при создании скрипта наличие базы данных сервера отчетов.  
  
 Созданный скрипт поддерживает [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
