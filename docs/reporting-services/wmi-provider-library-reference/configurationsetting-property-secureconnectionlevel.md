---
title: Свойство SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SecureConnectionLevel
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fdb8fc97b8b2403366e19456b7c744012ee9007f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570254"
---
# <a name="configurationsetting-property---secureconnectionlevel"></a>Свойство ConfigurationSetting — SecureConnectionLevel
  Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Значение **Integer** , представляющее уровень безопасного соединения. Возвращаемые значения указывают, была произведена настройка SSL или нет. Значение, которое больше или равно 1, указывает на то, что протокол SSL включен. Значение 0 указывает на то, что протокол SSL отключен.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks

В SQL Server 2008 R2 элемент SecureConnectionLevel является двухфазным переключателем. Дополнительные сведения см. в разделе [Метод ConfigurationSetting — SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setsecureconnectionlevel.md).

## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
