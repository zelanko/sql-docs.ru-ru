---
title: "Свойство DatabaseLogonType (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "DatabaseLogonType"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "DatabaseLogonType, свойство"
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
caps.latest.revision: 24
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство DatabaseLogonType (WMI MSReportServer_ConfigurationSetting)
  Определяет, какая учетная запись используется для доступа к базе данных сервера отчетов: учетная запись службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, учетная запись пользователя Windows, либо имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## Значения свойств  
 Объект **integer** представляет тип входа.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Замечания  
 Возможны следующие значения.  
  
-   0 для имени входа Windows  
  
-   1 для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 для входа в качестве службы  
  
 Если указывается значение 0 (Windows), в свойстве [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md) необходимо задать соответствующую учетную запись пользователя Windows.  
  
 Если указывается значение 1 (SQL Server), в свойстве [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md) должно быть задано допустимое имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если указывается значение 2 (служба Windows), сервер отчетов использует для доступа к своей базе данных учетную запись [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] и учетную запись службы Windows. Свойство DatabaseLogonAccount игнорируется.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  