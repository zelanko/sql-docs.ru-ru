---
title: Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
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
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8dac5ed639e3e06bbcf4ff11a5ea5b21cf03f24b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099517"
---
# <a name="listreservedurls-method-wmi-msreportserverconfigurationsetting"></a>Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)
  Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Application[]*  
 [out] Приложения, которые имеют резервирование URL-адресов.  
  
 *UrlString[]*  
 [out] Зарезервированные URL-адреса.  
  
 *Account[]*  
 [out] Имена учетной записи, связанные с учетной записью для резервирования URL-адресов.  
  
 *AccountSID[]*  
 [out] Идентификаторы безопасности, связанные с учетной записью для резервирования URL-адресов.  
  
 *Длина*  
 [out] Длина массивов, возвращаемых методом.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  