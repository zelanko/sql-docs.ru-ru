---
title: "Метод RemoveURL (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт"
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
helpviewer_keywords: RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: "13"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6b96a9374f5f25d07c7ba513ae63615b06fc83ba
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---removeurl"></a>Метод ConfigurationSetting — RemoveURL
  Удаляет URL-адрес, зарезервированный для сервера отчетов. Если нужно удалить несколько URL-адресов, это должно быть сделано одним вызовом данного API.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого удаляется резервирование.  
  
 *URLString*  
 URL-адрес для резервирования.  
  
 *lcid*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Ошибка*  
 [out] Описания возникших ошибок.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Замечания  
 *UrlString* не включает имя виртуального каталога — для этого есть [метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md).  
  
 Прежде чем вызывать метод [ReserveURL](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-reserveurl.md) , необходимо задать значение свойства конфигурации VirtualDirectory для параметра *Application* . Используйте [метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) для задания свойства VirtualDirectory.  
  
 Если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляют SSL-сертификат и он не нужен никаким другим URL-адресам, он удаляется.  
  
 Во время этой операции данный метод вызывает жесткую очистку и остановку всех доменов неконфигурационных приложений; после этой операции домены приложений перезапускаются.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также раздел  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
