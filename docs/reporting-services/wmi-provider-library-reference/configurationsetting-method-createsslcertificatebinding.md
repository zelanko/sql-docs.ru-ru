---
title: "Метод CreateSSLCertificateBinding (WMI MSReportServer_ConfigurationSetting) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
caps.latest.revision: 14
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1d9a797922bc8d7b39e7b7c43897d4ae5ee5bd28
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-method---createsslcertificatebinding"></a>Метод ConfigurationSetting - CreateSSLCertificateBinding
  Создает привязку SSL-сертификата.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого следует создать привязку к сертификату.  
  
 *CertificateHash*  
 Хэш для сертификата.  
  
 *IPAddress*  
 IP-адрес для приложения.  
  
 *Порт*  
 Порт SSL, связанный с привязкой.  
  
 *Код языка*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Ошибка*  
 [out] Описание случившихся ошибок.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Замечания  
 Этот метод позволяет добавить привязку приложения в файл rsreportserver.config. Если привязка еще не существует в файле HTTP.SYS, то она в нем создается.  
  
 Перед созданием привязки при вызове метода происходит проверка зарезервированных URL-адресов для того, чтобы указанное приложение могло определить допустимость привязки сертификата SSL.  
  
 Выполняется проверка следующих условий, результатом которой могут стать ошибки.  
  
1.  Сертификат не существует.  
  
2.  Указанный сертификат не соответствует значению, указанному для параметра IPAddress для этого компьютера.  
  
3.  Указанное значение параметра IPAddress является адресом категории DHCP IPAddress (изменение которого происходит периодически). Рекомендуется вместо указанного адреса использовать IP-адрес с подстановочными символами (0.0.0.0).  
  
4.  Указанное значение параметра IPAddress не соответствует IP-адресу, указанному в списке зарезервированных URL-адресов и не является подстановочным символом или именем хоста для существующего зарезервированного URL-адреса.  
  
5.  Наличие зарезервированного URL-адреса, определяющего, что имя хоста не совпадает с именем, указанным в сертификате имени хоста.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
