---
title: Свойство ConnectionPoolSize (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- ConnectionPoolSize
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ConnectionPoolSize property
ms.assetid: b80c8e5d-b725-4fe4-aec6-02fb18ec4434
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 589069aebe2275fd06e58385fd85cffaaa3c1222
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016135"
---
# <a name="connectionpoolsize-property-wmi-msreportserverconfigurationsetting"></a>Свойство ConnectionPoolSize (WMI MSReportServer_ConfigurationSetting)
  Размер пула соединений, используемого сервером отчетов для связи с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где находится база данных сервера отчетов. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim ConnectionPoolSize As UInt32  
```  
  
```csharp  
public UInt32 ConnectionPoolSize;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Доступное только для чтения **целое число** объект, который возвращает значение `768`.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
