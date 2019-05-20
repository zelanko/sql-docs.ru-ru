---
title: Метод GetDatabaseVersionDisplayName (WMI) | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4d29ed7bc6e627f7ed670feca9b98b0b4fac3eb9
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65570958"
---
# <a name="configurationsetting-method---getdatabaseversiondisplayname"></a>Метод ConfigurationSetting — GetDatabaseVersionDisplayName
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
  
## <a name="remarks"></a>Remarks  
 Следующая таблица показывает сопоставления версий базы данных с отображаемыми строками.  
  
|**Выпуск**|**Версия**|**Отображаемое имя**|  
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
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
