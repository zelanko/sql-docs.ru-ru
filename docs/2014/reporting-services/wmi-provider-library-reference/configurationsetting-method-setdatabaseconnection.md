---
title: Метод SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f722ac82f839b76bfb76d21d4a23aae884ade038
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66098103"
---
# <a name="setdatabaseconnection-method-wmi-msreportserverconfigurationsetting"></a>Метод SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting)
  Задает подключение к определенной базе данных сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Server*  
 Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещается база данных сервера отчетов.  
  
 *DatabaseName*  
 Имя базы данных сервера отчетов.  
  
 *CredentialsType*  
 Тип учетных данных, которые используются для соединения. Может принимать следующие значения:  
  
-   0 — Windows;  
  
-   1 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 — служба Windows.  
  
 *UserName*  
 Имя учетной записи, которая используется для соединения с базой данных сервера отчетов.  
  
 *Пароль*  
 Пароль, используемый для соединения с базой данных сервера отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Если параметр *CredentialsType* имеет значение 0 (Windows), необходимо указать значения параметров *UserName* и *Password* . Параметр *UserName* должен иметь вид "домен\имя_пользователя", значение должно представлять действующие данные для входа в Windows.  
  
 Если параметр *CredentialsType* имеет значение 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), то значение, передаваемое в параметре *UserName* , должно соответствовать требованиям, предъявляемым к имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если параметр *CredentialsType* имеет значение 2 (служба Windows), сервер отчетов использует встроенную безопасность для соединения с базой данных сервера отчетов, а параметры *UserName* и *Password* не учитываются. Для доступа к базе данных сервера отчетов веб-служба сервера отчетов использует либо учетную запись [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)], либо учетную запись пула приложений и учетную запись службы Windows.  
  
 При вызове метода SetDatabaseConnection учетные данные и сведения о базе данных зашифровываются и сохраняются в файле конфигурации для указанного сервера отчетов.  
  
 Метод SetDatabaseConnection не проверяет, может ли сервер отчетов соединиться с базой данных сервера отчетов с помощью указанных данных.  
  
 В первый раз свойство ConnectionPoolSize устанавливается в зависимости от количества процессоров: ConnectionPoolSize = число процессоров * 75.  
  
 Метод SetDatabaseConnection не предоставляет разрешения указанным учетным записям. Следует вызвать метод [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) для каждой учетной записи, которой требуется доступ к базе данных сервера отчетов, и запустить получившийся скрипт.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
