---
title: "Метод DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "DeleteEncryptedInformation, метод"
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting)
  Удаляет зашифрованные данные из базы данных сервера отчетов.  
  
## Синтаксис  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Параметры  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## Замечания  
 При вызове этого метода удаляются следующие данные.  
  
-   Зашифрованные сведения об источнике данных, в том числе имя пользователя и пароль.  
  
-   Данные о подписке, зашифрованные с помощью интерфейсов модуля доставки.  
  
-   Все сведения о таблице ключей в базе данных сервера отчетов.  
  
 После вызова этого метода пользователь должен инициализировать каждый компьютер, использующий базу данных сервера отчетов.  
  
 Вызов метода DeleteEncryptedInformation не затрагивает файл конфигурации сервера отчетов.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  