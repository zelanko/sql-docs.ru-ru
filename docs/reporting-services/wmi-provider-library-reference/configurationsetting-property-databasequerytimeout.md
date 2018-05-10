---
title: Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- DatabaseQueryTimeout Property
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 52b40c4c3df23d79f62baca4b3bb7af3f8cf88a3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
