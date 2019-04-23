---
title: Метод InitializeReportServer (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b4e01f1a0e6ab49939e3c8ad8339402a7d2b8431
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59961097"
---
# <a name="initializereportserver-method-wmi-msreportserverconfigurationsetting"></a>Метод InitializeReportServer (WMI MSReportServer_ConfigurationSetting)
  Инициализирует указанный экземпляр службы отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *InstallationID*  
 Строка, используемая для шифрования ключа шифрования перед его возвращением.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 При вызове этого метода ключ шифрования, который обращается к защищенным сведениям в базе данных сервера отчетов, зашифровывается с помощью открытого ключа сервера отчетов, определенного параметром *InstallationID*.  
  
 Указанный открытый ключ сервера отчетов должен быть предварительно записан в базу данных сервера отчетов.  
  
 Метод *InitializeReportServer* должен вызываться для сервера отчетов, который уже имеет доступ к защищенным сведениям, и поэтому может расшифровать ключ шифрования. Полученный зашифрованный ключ шифрования сохраняется в базе данных сервера отчетов.  
  
 Если сервер отчетов [IsInitialized](configurationsetting-property-isinitialized.md) свойству `true` при вызове метода InitializeReportServer, то метод завершается успешно без попытки зашифровать ключ шифрования.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
