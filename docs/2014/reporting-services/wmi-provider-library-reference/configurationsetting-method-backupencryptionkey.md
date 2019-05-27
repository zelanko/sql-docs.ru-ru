---
title: Метод BackupEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- BackupEncryptionKey method
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f31a95815c3a6c365d179a350846ec6f9a8bb795
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66098608"
---
# <a name="backupencryptionkey-method-wmi-msreportserverconfigurationsetting"></a>Метод BackupEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Создает резервную копию ключа шифрования для указанного экземпляра сервера отчетов. Ключ шифрования хранится в зашифрованном виде под защитой пароля.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```csharp  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *Пароль*  
 Строка, используемая для шифрования ключа шифрования перед его возвращением.  
  
 *KeyFile[]*  
 [out] Массив, содержащий зашифрованный ключ шифрования.  
  
 *Длина*  
 [out] Длина массива, возвращаемого методом.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
