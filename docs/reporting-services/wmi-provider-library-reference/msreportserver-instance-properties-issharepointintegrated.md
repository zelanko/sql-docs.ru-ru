---
title: "Свойство IsSharePointIntegrated (WMI MSReportServer_Instance) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a4a86ce7dbb8336aaa70cb2f93debe5dd7f9f70f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="msreportserverinstance-properties---issharepointintegrated"></a>Свойства MSReportServer_Instance - IsSharePointIntegrated
  Указывает, находится ли сервер отчетов в режиме интеграции с SharePoint. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], это свойство всегда возвращает значение **False** , поскольку в режиме интеграции с SharePoint экземпляры служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] являются совместно используемыми службами SharePoint, которые не управляются поставщиками WMI.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Значение **Boolean** показывает, работает ли сервер отчетов в режиме интеграции с SharePoint.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
