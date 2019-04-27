---
title: Метод SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ab5c414ec780c44cb8482ef85ae2032eaa54637
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646842"
---
# <a name="setemailconfiguration-method-wmi-msreportserverconfigurationsetting"></a>Метод SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>Примечания  
 Когда *SendUsingSMTPServer* параметр имеет значение `true`, **SendUsing** запись в файле конфигурации сервера отчетов имеет значение 1. Когда *SendUsingSMTPServer* присваивается `false`, **SendUsing** запись не настроена.  
  
 Этот метод не позволяет пользователям задать для записи **SendUsing** в файле конфигурации сервера отчетов какое-либо значение, кроме 1. Чтобы настроить на сервере отчетов почтовый протокол, отличный от SMTP, необходимо изменить файл конфигурации вручную.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
