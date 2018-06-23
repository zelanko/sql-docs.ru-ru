---
title: Метод ReserveURL (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 1cd5ef5a1e4a29b70d742e858a30ab9912cce6bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193728"
---
# <a name="reserveurl-method-wmi-msreportserverconfigurationsetting"></a>Метод ReserveURL (WMI MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>Примечания  
 Строка*UrlString* не включает имя виртуального каталога. [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) метод предоставляется для этой цели.  
  
 Для текущей учетной записи службы Windows создаются зарезервированные URL-адреса. Изменение учетной записи Windows требует обновления всех зарезервированных URL-адресов вручную.  
  
 Этот метод вызывает жесткую очистку всех доменов приложений. После завершения этой операции выполняется перезапуск всех доменов приложений.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  