---
title: Метод ListInstalledSharePointVersions (WMI) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2a29d73639a811a3f79ce579f98138449a8dbf5
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43280729"
---
# <a name="configurationsetting-method---listinstalledsharepointversions"></a>Метод ConfigurationSetting — ListInstalledSharePointVersions
  Возвращает набор токенов, представляющих версии Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленного на том же компьютере, что и сервер отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *[VersionTokens]*  
 [out] Массив, который содержит токены, представляющие версию продукта или технологии SharePoint, совместимых с установленным сервером отчетов.  
  
 *Длина*  
 [out] Длина массива токенов версии.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Каждый возвращенный токен представляет версию [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] или [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] , совместимую с установленным в настоящий момент сервером отчетов. Если версия SharePoint совместима с предыдущими версиями SharePoint, возвращаются токены для каждой совместимой версии SharePoint.  
  
 Ниже приведена таблица с возвращаемыми токенами SharePoint.  
  
|**Токены версий**|**Описание**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|Установлен экземпляр [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , совместимый с [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.|  
|WSS_V3_Compatible|Установлен экземпляр [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , совместимый с [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.|  
|WSS_V4_Compatible|Установлен экземпляр [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , совместимый с Office 14.|  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
