---
title: Метод ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef1a23d21e5945e15d497bab3480b48f8cf3fe6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098212"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a>Метод ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting)
  Создает новый ключ шифрования и повторно зашифровывает с его помощью всю защищенную информацию в каталоге.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *СОСТАВ*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *Екстендедеррорс []*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Метод ReencryptSecureInformation позволяет администратору заменить существующий ключ шифрования новым ключом.  
  
 При вызове этого метода сервер отчетов создает новый ключ шифрования и проходит по всему зашифрованному содержимому для его повторного шифрования с использованием нового ключа.  
  
 В модулях доставки защищенные сведения могут храниться в структуре параметров доставки. При вызове метода ReencryptSecureInformation сервер отчетов загружает каждую подписку и соответствующий модуль доставки и повторно зашифровывает сведения, которые хранятся в связанных параметрах.  
  
 Если этот метод запускается на компьютерах масштабного развертывания, то каждый компьютер потребует повторной инициализации.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
