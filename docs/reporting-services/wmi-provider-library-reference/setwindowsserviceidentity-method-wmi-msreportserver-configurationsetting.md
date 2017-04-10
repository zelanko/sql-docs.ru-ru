---
title: "Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "SetWindowsServiceIdentity, метод"
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Обеспечивает запуск службы Windows сервера отчетов в качестве заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.  
  
## Синтаксис  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## Параметры  
 *UseBuiltInAccount*  
 Показывает, является ли указанная учетная запись встроенной учетной записью Windows.  
  
 *Учетная запись*  
 Учетная запись Windows, которая используется для запуска службы Windows, имеет формат «ДОМЕН\псевдоним».  
  
 *Пароль*  
 Пароль для учетной записи.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## Замечания  
 Если параметру *UseBuiltInAccount* присвоено значение **true**, а сервер отчетов работает под управлением Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] или Windows XP, то значения параметров *Имя*, *Домен* и *Пароль* не учитываются, и используется учетная запись "Local System".  
  
 Если параметру *UseBuiltInAccount* присвоено значение **true** и сервер отчетов работает под управлением Windows Server 2003, то свойства *Домен* и *Пароль* не учитываются, а в поле имени должно быть значение "Builtin\NetworkService", "Builtin\System" или "Builtin\LocalService".  
  
 Метод SetWindowsServiceIdentity задает разрешения для файлов и папок в установочном каталоге сервера отчетов.  
  
 Учетная запись, указанная в параметре *Account* , запрашивает права **LogonAsService** в Windows. Метод предоставляет эти права указанной учетной записи.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  