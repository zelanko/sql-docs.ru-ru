---
title: Метод ReserveURL (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
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
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 73d4e96fc840b703521844e1f575164a2be7807e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configurationsetting-method---reserveurl"></a>Метод ConfigurationSetting — ReserveURL
  Добавляет резервирование URL-адресов для заданного приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого резервируется URL-адрес.  
  
 *UrlString*  
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
 Строка*UrlString* не включает имя виртуального каталога. Метод [SetVirtualDirectory](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) служит специально для этой цели.  
  
 Для текущей учетной записи службы Windows создаются зарезервированные URL-адреса. Изменение учетной записи Windows требует обновления всех зарезервированных URL-адресов вручную.  
  
 Этот метод вызывает жесткую очистку всех доменов приложений. После завершения этой операции выполняется перезапуск всех доменов приложений.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
