---
description: Свойство IsSharePointIntegrated (WMI MSReportServer_Instance)
title: Свойство IsSharePointIntegrated (WMI MSReportServer_Instance) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: abb93d7f4e98009916228e1cb4daf239913d003c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "92255525"
---
# <a name="msreportserver_instance-properties---issharepointintegrated"></a>Свойства MSReportServer_Instance — IsSharePointIntegrated
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
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
