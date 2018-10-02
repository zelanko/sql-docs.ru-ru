---
title: Метод SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9d28e2a460340985d771924d1c8c88559dfd08cf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759773"
---
# <a name="configurationsetting-method---setsecureconnectionlevel"></a>Метод ConfigurationSetting — SetSecureConnectionLevel
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
  
## <a name="remarks"></a>Remarks  
 При вызове метода свойство SecureConnectionLevel сервера отчетов получает заданное значение. Значение 0 указывает на то, что протокол SSL отключен. Значение, которое больше или равно 1, указывает на то, что протокол SSL включен.  
  
-   Если значение задано, то элемент SecureConnectionLevel в файле конфигурации сервера отчетов изменился, а к элементу **URLRoot** в файле конфигурации добавляется "https://", если указанное значение параметра *Level* больше или равно 1, либо "http://", если указанное значение параметра *Level* равно 0.  
  
 В [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]элемент SecureConnectionLevel является двухфазным переключателем. Значение по умолчанию равно 0. Для любого значения, которое больше или равно 1, переданного через API метода SetSecureConnectionLevel, SSL считается включенным, а свойство конфигурации SecureConnectionLevel в файле rsreportserver.config задается соответственно. Значения 2 и 3 по-прежнему разрешены для обеспечения обратной совместимости.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
