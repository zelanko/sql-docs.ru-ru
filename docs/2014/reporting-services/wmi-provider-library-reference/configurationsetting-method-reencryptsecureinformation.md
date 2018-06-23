---
title: Метод ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
caps.latest.revision: 18
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 74727f725f21e646213f6015cc08f7422699bc8c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101008"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserverconfigurationsetting"></a>Метод ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting)
  Создает новый ключ шифрования и повторно зашифровывает с его помощью всю защищенную информацию в каталоге.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Метод ReencryptSecureInformation позволяет администратору заменить существующий ключ шифрования новым ключом.  
  
 При вызове этого метода сервер отчетов создает новый ключ шифрования и проходит по всему зашифрованному содержимому для его повторного шифрования с использованием нового ключа.  
  
 В модулях доставки защищенные сведения могут храниться в структуре параметров доставки. При вызове метода ReencryptSecureInformation сервер отчетов загружает каждую подписку и соответствующий модуль доставки и повторно зашифровывает сведения, которые хранятся в связанных параметрах.  
  
 Если этот метод запускается на компьютерах масштабного развертывания, то каждый компьютер потребует повторной инициализации.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  