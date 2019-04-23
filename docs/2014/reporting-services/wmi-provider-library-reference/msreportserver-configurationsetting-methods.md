---
title: Методы MSReportServer_ConfigurationSetting | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- MSReportServer_ConfigurationSetting Methods
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], MSReportServer_ConfigurationSetting class
- MSReportServer_ConfigurationSetting class
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e9abd4e72182bb649eb608a2f7a7e2bef7044f9
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59936941"
---
# <a name="msreportserverconfigurationsetting-methods"></a>Методы MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting поставщика WMI сервера отчетов содержит следующие общие методы.  
  
## <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Создает резервную копию ключа шифрования для экземпляра. Ключ шифрования хранится в зашифрованном виде под защитой пароля.|  
|[CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-createsslcertificatebinding.md)|Создает привязку SSL-сертификата.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Удаляет зашифрованные данные из базы данных сервера отчетов.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Удаляет ключи шифрования из базы данных сервера отчетов.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Формирует скрипт SQL, с помощью которого можно предоставить пользователю разрешения для базы данных сервера отчетов.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Формирует скрипт SQL, который можно использовать для обновления базы данных сервера отчетов.|  
|[Метод GetAdminSiteUrl (WMI)](configurationsetting-method-getadminsiteurl.md)|Возвращает абсолютный URL-адрес веб-сайта центра администрирования.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Инициализирует заданный экземпляр сервера отчетов.|  
|[Метод ListInstalledSharePointVersions (WMI)](configurationsetting-method-listinstalledsharepointversions.md)|Возвращает набор токенов, представляющих версии Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленных на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listipaddresses.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listreservedurls.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listsslcertificatebindings.md)|Выводит список привязок SSL-сертификатов, существующих в таблице компонента HTTP.SYS, и привязок, ожидаемых в файле RSReportServer.config.|  
|[Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listsslcertificates.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-removesslcertificatebinding.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-removeurl.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-reserveurl.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Указывает время ожидания по умолчанию для запросов базы данных сервера отчетов.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Включает и отключает службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Обеспечивает запуск службы сервера отчетов как заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.|  
  
## <a name="see-also"></a>См. также  
 [MSReportServer_ConfigurationSetting Class](msreportserver-configurationsetting-class.md)  
  
  
