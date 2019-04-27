---
title: Метод SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d78cd09c03f6507bdb87cda4c47e8132f2e1f9b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646370"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserverconfigurationsetting"></a>Метод SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Задает уровень безопасных соединений для сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Level*  
 Целое значение, представляющее уровень безопасного соединения.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 При вызове метода свойство SecureConnectionLevel сервера отчетов получает заданное значение. Значение 0 указывает на то, что протокол SSL отключен. Значение, которое больше или равно 1, указывает на то, что протокол SSL включен.  
  
-   Если значение задано, то элемент SecureConnectionLevel в файле конфигурации сервера отчетов изменяется и `URLRoot` элемент в файле конфигурации настроен на использование « https://», если указанный *уровень* больше, чем или равно 1, либо « http://», если указанный *уровень* равно 0.  
  
 В [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]элемент SecureConnectionLevel является двухфазным переключателем. Значение по умолчанию равно 0. Для любого значения, которое больше или равно 1, переданного через API метода SetSecureConnectionLevel, SSL считается включенным, а свойство конфигурации SecureConnectionLevel в файле rsreportserver.config задается соответственно. Значения 2 и 3 по-прежнему разрешены для обеспечения обратной совместимости.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
