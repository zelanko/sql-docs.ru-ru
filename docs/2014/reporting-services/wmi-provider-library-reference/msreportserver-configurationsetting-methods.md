---
title: Методы MSReportServer_ConfigurationSetting | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
ms.openlocfilehash: 6d3fc7ae8ad4c3018bcc512296a670fdaac3b64e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097358"
---
# <a name="msreportserver_configurationsetting-methods"></a>Методы MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting поставщика WMI сервера отчетов содержит следующие общие методы.  
  
## <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Создает резервную копию ключа шифрования для экземпляра. Ключ шифрования хранится в зашифрованном виде под защитой пароля.|  
|[Метод CreateSSLCertificateBinding &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-createsslcertificatebinding.md)|Создает привязку SSL-сертификата.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Удаляет зашифрованные данные из базы данных сервера отчетов.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Удаляет ключи шифрования из базы данных сервера отчетов.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Формирует скрипт SQL, с помощью которого можно предоставить пользователю разрешения для базы данных сервера отчетов.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Формирует скрипт SQL, который можно использовать для обновления базы данных сервера отчетов.|  
|[Метод GetAdminSiteUrl &#40;WMI&#41;](configurationsetting-method-getadminsiteurl.md)|Возвращает абсолютный URL-адрес веб-сайта центра администрирования.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Инициализирует заданный экземпляр сервера отчетов.|  
|[Метод ListInstalledSharePointVersions &#40;WMI&#41;](configurationsetting-method-listinstalledsharepointversions.md)|Возвращает набор токенов, представляющих [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]версии Microsoft, [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленные на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-listipaddresses.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-listreservedurls.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-listsslcertificatebindings.md)|Выводит список привязок SSL-сертификатов, существующих в таблице компонента HTTP.SYS, и привязок, ожидаемых в файле RSReportServer.config.|  
|[Метод ListSSLCertificates &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-listsslcertificates.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-removesslcertificatebinding.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-removeurl.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-reserveurl.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Указывает время ожидания по умолчанию для запросов базы данных сервера отчетов.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Включает и отключает службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-setvirtualdirectory.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Обеспечивает запуск службы сервера отчетов как заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.|  
  
## <a name="see-also"></a>См. также:  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  
