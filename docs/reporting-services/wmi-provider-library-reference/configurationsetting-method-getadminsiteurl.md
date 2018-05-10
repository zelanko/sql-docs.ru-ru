---
title: Метод GetAdminSiteUrl (WMI) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6e11c5ab69787b4a07eccdf7a8c33943c1e7ec01
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configurationsetting-method---getadminsiteurl"></a>Метод ConfigurationSetting — GetAdminSiteUrl
  Возвращает абсолютный URL-адрес веб-сайта центра администрирования фермы Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , с которой интегрирован сервер отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *AdminSiteUrl*  
 [out] Строка, содержащая абсолютный URL-адрес веб-сайта центра администрирования фермы SharePoint, с которой интегрирован сервер отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Методы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  
