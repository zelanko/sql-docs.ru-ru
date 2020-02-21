---
title: Метод SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3e2b3e3c1d3d9fc5193a8c87c2aa96f9ff2d3ba2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65581011"
---
# <a name="configurationsetting-method---setemailconfiguration"></a>Метод ConfigurationSetting — SetEmailConfiguration
  Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *SendUsingSMTPServer*  
 Логическое значение. Показывает, должен ли сервер отправлять почту с помощью SMTP-сервера. Этот может принимать только значение true. Значение по умолчанию — false.  
  
 *SMTPServer*  
 Строка, которая содержит имя или IP-адрес SMTP-сервера.  
  
 *SenderEmailAddress*  
 Адрес электронной почты, используемый в поле «От:» в сообщениях, отправленных с сервера отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Когда значение параметра *SendUsingSMTPServer* становится равным **true**, запись **SendUsing** в файле конфигурации сервера отчетов изменяет значение на 1. Когда параметр *SendUsingSMTPServer* приобретает значение **false**, запись **SendUsing** не настраивается.  
  
 Этот метод не позволяет пользователям задать для записи **SendUsing** в файле конфигурации сервера отчетов какое-либо значение, кроме 1. Чтобы настроить на сервере отчетов почтовый протокол, отличный от SMTP, необходимо изменить файл конфигурации вручную.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
