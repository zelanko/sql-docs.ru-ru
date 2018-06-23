---
title: Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fc3dfeafab01480fde7eb195363f46946de30ddd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180186"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Обеспечивает запуск службы Windows сервера отчетов в качестве заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *UseBuiltInAccount*  
 Показывает, является ли указанная учетная запись встроенной учетной записью Windows.  
  
 *Учетная запись*  
 Учетная запись Windows, которая используется для запуска службы Windows, имеет формат «ДОМЕН\псевдоним».  
  
 *Пароль*  
 Пароль для учетной записи.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Когда *UseBuiltInAccount* параметра равным `true` и сервер отчетов работает под управлением Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] или Windows XP, значение *имя*, *домена*, и *пароль* учитываются и используется учетная запись локальной системы.  
  
 При *UseBuiltInAccount* параметра равным `true` и сервер отчетов работает в Windows Server 2003 *домена* и *пароль* свойства не учитывается, и должен содержать поля «имя», «Builtin\NetworkService» или «Builtin\System» или «Builtin\LocalService».  
  
 Метод SetWindowsServiceIdentity задает разрешения для файлов и папок в установочном каталоге сервера отчетов.  
  
 Учетная запись, указанная в *учетной записи* параметра должно быть `LogonAsService` правами в Windows. Метод предоставляет эти права указанной учетной записи.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  