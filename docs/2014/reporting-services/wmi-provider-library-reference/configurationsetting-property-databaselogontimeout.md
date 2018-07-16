---
title: Свойство DatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
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
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
caps.latest.revision: 37
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b93c42c786707f11144b06e1da55569b05701fae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257900"
---
# <a name="databaselogontimeout-property-wmi-msreportserverconfigurationsetting"></a>Свойство DatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting)
  Указывает число секунд ожидания перед тем, как попытка входа в базу данных сервера отчетов признается неуспешной. Значение **0** указывает на бесконечное время ожидания. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a>Значения свойств  
 32-разрядное целое число со знаком, представляющее количество секунд.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
