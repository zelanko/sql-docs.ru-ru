---
title: Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 886c6b6622a2051751704aa9ea72aabcbb4afef3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579907"
---
# <a name="configurationsetting-method---listreservedurls"></a>Метод ConfigurationSetting — ListReservedURLs
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
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
