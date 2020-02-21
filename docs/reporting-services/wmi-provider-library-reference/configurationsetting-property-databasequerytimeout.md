---
title: Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseQueryTimeout Property
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8149c0954195796ce71a48e022a2f7bc83471601
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65573585"
---
# <a name="configurationsetting-property---databasequerytimeout"></a>Свойство ConfigurationSetting — DatabaseQueryTimeout
  Задает число секунд, которое должно пройти до того, как сервер отчетов предположит, что при выполнении команды произошла ошибка или выполнение заняло слишком много времени. Сервер отчетов привязывает запросы по времени к каталогу SQL, а не к источнику данных для отчета. Read/write.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Объект 32-разрядного беззнакового **целого числа** , показывающий время в секундах, которое отводится на выполнение запроса.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
