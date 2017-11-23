---
title: "Использование шифрования без проверки | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d29061f3c43735b9a3855cee0dd635face3db00
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="using-encryption-without-validation"></a>Использование шифрования без проверки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] всегда шифрует сетевые пакеты, связанные со входом в систему. Если сертификат не был предоставлен на сервере при запуске, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает самозаверенный сертификат, который используется для шифрования пакетов входа.  
  
 Приложения могут также запрашивать шифрование всего сетевого трафика путем использования ключевых слов строк соединения или свойств соединения. Ключевые слова являются «Encrypt» для ODBC и OLE DB, при использовании строки поставщика с **IDbInitialize::Initialize**, или «Use Encryption for Data» для ADO и OLE DB при использовании строки инициализации с **IDataInitialize** . Это также может быть настроен по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager с помощью **принудительное шифрование протокола** параметр. По умолчанию для шифрования всего сетевого трафика соединения требуется, чтобы сертификат присутствовал на сервере.  
  
 Сведения о ключевых словах строки соединения см. в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Чтобы включить шифрование для использования, если сертификат не был предоставлен на сервере, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager может использоваться для установки как **принудительное шифрование протокола** и **доверять сертификату сервера**  параметры. В этом случае шифрование будет использовать самозаверяющий сертификат сервера, не проверяя наличия подтверждаемого сертификата сервера.  
  
 Приложения могут также использовать ключевое слово «TrustServerCertificate» или его атрибут связанного соединения, чтобы гарантировать применение шифрования. Параметры приложения никогда не снижают уровень безопасности, установленный клиентским диспетчером конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], но могут повысить его. Например если **принудительное шифрование протокола** не задано для клиента, приложение может само запросить шифрование. Чтобы гарантировать применение шифрования, даже если сертификат сервера не был предоставлен, приложение может запросить шифрование и ключевое слово «TrustServerCertificate». Однако если ключевое слово «TrustServerCertificate» не включено в конфигурации клиента, предоставление сертификата сервера по-прежнему необходимо. В следующей таблице описываются все случаи:  
  
|Параметр «Принудительное шифрование протокола» на клиенте|Параметр «Доверять сертификату сервера» на клиенте|Строка соединения или атрибут соединения «Шифрование/использовать шифрование для данных»|Строка соединения или атрибут соединения «Надежный сертификат сервера»|Результат|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|Нет|Недоступно|Нет (по умолчанию)|Не учитывается|Шифрование отсутствует.|  
|Нет|Недоступно|Да|Нет (по умолчанию)|Шифрование применяется только при наличии подтверждаемого сертификата сервера, в противном случае попытка соединения завершается неудачно.|  
|Нет|Недоступно|Да|Да|Шифрование производится всегда, однако при этом может использоваться самозаверяющий сертификат сервера.|  
|Да|Нет|Не учитывается|Не учитывается|Шифрование применяется только при наличии подтверждаемого сертификата сервера, в противном случае попытка соединения завершается неудачно.|  
|Да|Да|Нет (по умолчанию)|Не учитывается|Шифрование производится всегда, однако при этом может использоваться самозаверяющий сертификат сервера.|  
|Да|Да|Да|Нет (по умолчанию)|Шифрование применяется только при наличии подтверждаемого сертификата сервера, в противном случае попытка соединения завершается неудачно.|  
|Да|Да|Да|Да|Шифрование производится всегда, однако при этом может быть использован самозаверяющий сертификат сервера.|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает шифрование без проверки путем добавления SSPROP_INIT_TRUST_SERVER_CERTIFICATE свойство инициализации источника данных, которая реализована в свойство DBPROPSET_SQLSERVERDBINIT набор. Кроме того, добавлено новое ключевое слово строки соединения «TrustServerCertificate». Оно принимает значения «yes» и «no», значение по умолчанию — «no». При использовании компонентов службы оно принимает значения true и false, значение по умолчанию — false.  
  
 Дополнительные сведения об улучшениях, появившихся в наборе свойств dbpropset_sqlserverdbinit см. в разделе [свойства инициализации и авторизации](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает шифрование без проверки путем добавления к [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) и [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) функции. Добавлен параметр SQL_COPT_SS_TRUST_SERVER_CERTIFICATE, который может принимать значения SQL_TRUST_SERVER_CERTIFICATE_YES или SQL_TRUST_SERVER_CERTIFICATE_NO, где SQL_TRUST_SERVER_CERTIFICATE_NO является значением по умолчанию. Кроме того, добавлено новое ключевое слово строки соединения «TrustServerCertificate». Оно принимает значения «yes» и «no», значение по умолчанию — «no».  
  
## <a name="see-also"></a>См. также:  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
