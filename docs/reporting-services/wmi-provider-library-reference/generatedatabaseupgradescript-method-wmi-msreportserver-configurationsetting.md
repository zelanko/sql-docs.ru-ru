---
title: "Метод GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "GenerateDatabaseUpgradeScript, метод"
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
caps.latest.revision: 22
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting)
  Формирует скрипт, который можно использовать для обновления базы данных сервера отчетов до схемы [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .  
  
## Синтаксис  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## Параметры  
 *Databasename*  
 Строка, которая содержит имя базы данных сервера отчетов для обновления.  
  
 *ServerVersion*  
 Строка, которая содержит версию сервера отчетов.  
  
 *Скрипт*  
 [out] Строка, содержащая сформированный скрипт SQL.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## Замечания  
 Созданный скрипт поддерживает [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  