---
title: Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e68bb7c70d08fb07d3079436fafe5fd61ae104f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097921"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a>Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)
  Задает имя виртуального каталога для указанного приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого задается виртуальный каталог.  
  
 *VirtualDirectory*  
 Имя виртуального каталога.  
  
 *намного*  
 Идентификатор локали для виртуального каталога.  
  
 *Ошибка*  
 [out] Описания возникших ошибок.  
  
 *СОСТАВ*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Для приложения можно задать только одно имя виртуального каталога для всех зарезервированных URL-адресов.  
  
 Параметр VirtualDirectory должен соответствовать контексту именования для виртуальных каталогов. Параметр VirtualDirectory не должен быть пустой строкой.  
  
 Обновляет значение элемента \Configuration\URLReservations\Application\VirtualDirectory. Выполняется успешно, даже еще не созданы зарезервированные URL-адреса.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
