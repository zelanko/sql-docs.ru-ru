---
title: Метод GetDatabaseVersionDisplayName (WMI) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 86d5e6d39e851e86320c52e989cb27d5e53b055d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222644"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a>Метод GetDatabaseVersionDisplayName (WMI)
  Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Версия*  
 Строка, содержащая строку версии базы данных сервера отчетов.  
  
 *DisplayName*  
 [out] Строка, содержащая отображаемое имя, соответствующее заданной версии.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="remarks"></a>Примечания  
 Следующая таблица показывает сопоставления версий базы данных с отображаемыми строками.  
  
|**Выпуск**|`Version`|**Отображаемое имя**|  
|-----------------|-----------------|----------------------|  
|Службы Reporting Services 2005 с пакетом обновления 2 (SP2)|@DBVersion = 'C.0.8.54'|SQL Server 2005 SP2|  
|Службы Reporting Services 2005 с пакетом обновления 1 (SP1)|@DBVersion = 'C.0.8.43'|SQL Server 2005 SP1|  
|Службы Reporting Services 2005, RTM-версия|@DBVersion = 'C.0.8.40'|SQL Server 2005|  
|Службы Reporting Services 2000 с пакетом обновления 2 (SP2)|@DBVersion = 'C.0.6.54'|SQL Server 2000 с пакетом обновления 2 (SP2)|  
|Службы Reporting Services 2000 с пакетом обновления 1 (SP1)|@DBVersion = 'C.0.6.51'|SQL Server 2000 SP1|  
|Службы Reporting Services 2000, RTM-версия|@DBVersion = 'C.0.6.43'|SQL Server 2000|  
|Исправление||Ближайшая применимая версия|  
  
 Для *версий* , предшествующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000, возвращается значение типа HRESULT параметра ACT_E_BAD_VERSION.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
