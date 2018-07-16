---
title: Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2cf7248fe0052a23e3ceef2243a4b6b45645402b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258000"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting)
  Задает число секунд, которое должно пройти до того, как сервер отчетов предположит, что при выполнении команды произошла ошибка или выполнение заняло слишком много времени. Сервер отчетов привязывает запросы по времени к каталогу SQL, а не к источнику данных для отчета. Read/write.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Значения свойств  
 32-разрядного беззнакового `integer` , представляющий количество секунд, запрос может выполняться.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
