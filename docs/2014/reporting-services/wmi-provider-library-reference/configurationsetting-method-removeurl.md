---
title: Метод RemoveURL (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c9ab7dc3ea75201bd011b85f80169d50e2ba0d37
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52518893"
---
# <a name="removeurl-method-wmi-msreportserverconfigurationsetting"></a>Метод RemoveURL (WMI MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>Remarks  
 *UrlString* не включает имя виртуального каталога — для этого есть [метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md).  
  
 Прежде чем вызывать метод [ReserveURL](configurationsetting-method-reserveurl.md) , необходимо задать значение свойства конфигурации VirtualDirectory для параметра *Application* . Используйте [метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) для задания свойства VirtualDirectory.  
  
 Если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляют SSL-сертификат и он не нужен никаким другим URL-адресам, он удаляется.  
  
 Во время этой операции данный метод вызывает жесткую очистку и остановку всех доменов неконфигурационных приложений; после этой операции домены приложений перезапускаются.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
