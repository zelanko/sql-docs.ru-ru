---
title: Метод SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
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
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
caps.latest.revision: 19
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 67d63332e69e42b3f8631d37fe24626e108dde14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179984"
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
 Когда *SendUsingSMTPServer* параметра равным `true`, **SendUsing** запись в файл конфигурации сервера отчетов имеет значение 1. Когда *SendUsingSMTPServer* равно `false`, **SendUsing** запись не настроена.  
  
 Этот метод не позволяет пользователям задать для записи **SendUsing** в файле конфигурации сервера отчетов какое-либо значение, кроме 1. Чтобы настроить на сервере отчетов почтовый протокол, отличный от SMTP, необходимо изменить файл конфигурации вручную.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  