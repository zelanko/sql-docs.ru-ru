---
title: Постоянное шифрование Справочник по API для драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 1/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f5c67ad5add796f151e5b86c7c5ab8b8fc82118
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Постоянное шифрование Справочник по API для драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Функция Always Encrypted позволяет клиентам шифровать конфиденциальные данные в клиентских приложениях, не раскрывая ключи шифрования для SQL Server. Драйвер с поддержкой Always Encrypted, установленный на клиентском компьютере, реализует это за счет автоматического шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер шифрует данные из конфиденциальных столбцов перед их передачей в SQL Server и автоматически переписывает запросы, чтобы сохранить семантику приложения. Аналогичным образом драйвер прозрачно расшифровывает данные, хранящиеся в столбцах зашифрованной базы данных, которые содержатся в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [использование постоянного шифрования с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Постоянное шифрование — поддерживается только Microsoft JDBC Driver 6.0 или более поздней версии для SQL Server с SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Постоянное шифрование ссылки на API-Интерфейс
 
 Существует несколько дополнений и изменений для API драйвера JDBC для использования в клиентских приложениях, использующих функцию Always Encrypted.  
  
 **Класс SQLServerConnection**  
  
|Название|Описание|  
|----------|-----------------|  
|Новое ключевое слово строки подключения:<br /><br /> columnEncryptionSetting|columnEncryptionSetting = Enabled включает постоянное шифрование для подключения, а columnEncryptionSetting = Disabled отключает его. Допустимыми являются значения Enabled/Disabled. По умолчанию установлено значение Disabled.|  
|Новые методы:<br /><br /> открытые статические setColumnEncryptionTrustedMasterKeyPaths void (карта < String, список\<строка >> trustedKeyPaths)<br /><br /> открытые статические updateColumnEncryptionTrustedMasterKeyPaths void (список строка сервера\<строка > trustedKeyPaths)<br /><br /> void removeColumnEncryptionTrustedMasterKeyPaths открытые статические (строка server)|Позволяет выполнять набор/обновления/удаления список доверенных путей ключа для сервера базы данных. Если при обработке запроса приложения драйвер получает путь ключа, которого нет в списке, запрос завершается с ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление скомпрометированным SQL Server фиктивных путей ключа, что может привести к утечке учетных данных хранилища ключей.|  
|Новый метод:<br /><br /> открытые статические карты < String, список\<строка >> getColumnEncryptionTrustedMasterKeyPaths()|Возвращает список доверенных путей ключа для сервера базы данных.|  
|Новый метод:<br /><br /> открытые статические registerColumnEncryptionKeyStoreProviders void (карты\<String, SQLServerColumnEncryptionKeyStoreProvider > clientKeyStoreProviders)|Позволяет регистрировать пользовательские поставщики хранилища ключей. Это словарь, сопоставляющий имена поставщиков хранилища ключей с реализациями поставщиков хранилища ключей.<br /><br /> Для использования хранилища ключей виртуальной машины Java необходимо создать экземпляр объекта SQLServerColumnEncryptionJVMKeyStoreProvider с помощью учетных данных хранилища ключей виртуальной машины Java и зарегистрировать его с помощью драйвера. Имя для этого поставщика должно быть «MSSQL_JVM_KEYSTORE».<br /><br /> Для использования хранилища хранилище ключей Azure необходимо создать экземпляр объекта SQLServerColumnEncryptionAzureKeyStoreProvider и зарегистрируйте его в драйвере. Имя для этого поставщика должно быть «AZURE_KEY_VAULT».|
|открытые окончательного логическое getSendTimeAsDatetime()|Возвращает значение свойства соединения sendTimeAsDatetime.|
|открытые void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)|Изменяет свойства sendTimeAsDatetime соединения.|

 **Класс SQLServerConnectionPoolProxy**
|Название|Описание|  
|----------|-----------------|  
|открытые окончательного логическое getSendTimeAsDatetime()|Возвращает значение свойства соединения sendTimeAsDatetime.|
|открытые void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)|Изменяет свойства sendTimeAsDatetime соединения.|
     
  
 **Класс SQLServerDataSource**  
  
|Название|Описание|  
|----------|-----------------|  
|открытый setColumnEncryptionSetting void (строка columnEncryptionSetting)|Включает или отключает функцию Always Encrypted для объекта источника данных.<br /><br /> По умолчанию установлено значение Disabled.|  
|открытый getColumnEncryptionSetting() строки|Получает параметр функции Always Encrypted для объекта источника данных.|
|открытый setKeyStoreAuthentication void (строка keyStoreAuthentication)|Задает имя, которое идентифицирует хранилище ключей. Значение, поддерживаемое является «JavaKeyStorePassword» для identifiying хранилище ключей Java.<br/><br/>Значение по умолчанию — NULL.|
|открытый getKeyStoreAuthentication() строки|Возвращает значение параметра keyStoreAuthentication для объекта источника данных.|
|открытый setKeyStoreSecret void (строка keyStoreSecret)|Задает пароль для ключей Java. Обратите внимание, что для поставщика хранилища ключей Java пароль для ключей и ключа должны совпадать. Обратите внимание, что необходимо установить keyStoreAuthentication со «JavaKeyStorePassword».|
|открытый setKeyStoreLocation void (строка keyStoreLocation)|Задает расположение, включая имя файла для хранилище ключей Java. Обратите внимание, что необходимо установить keyStoreAuthentication со «JavaKeyStorePassword».|
|открытый getKeyStoreLocation() строки|Извлекает keyStoreLocation для хранилища ключей Java.|
  
 **Класс SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Реализация поставщика хранилища ключей для хранилища ключей Java. Этот класс позволяет использовать сертификаты, находящиеся в хранилище ключей Java в качестве главных ключей столбца.  
  
 Конструкторы  
  
|Название|Описание|  
|----------|-----------------|  
|открытый SQLServerColumnEncryptionJavaKeyStoreProvider (строка keyStoreLocation, keyStoreSecret char [])|Поставщик хранилища ключей для хранилища ключей Java.|  
  
 Методы  
  
|Название|Описание|  
|----------|-----------------|  
|открытые byte [] decryptColumnEncryptionKey (masterKeyPath строка, строка encryptionAlgorithm, encryptedColumnEncryptionKey byte [])|Расшифровывает указанное зашифрованное значение ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Формат пути к ключу должен быть одним из следующих:**<br /><br /> Отпечаток: <отпечаток_сертификата><br /><br /> Псевдоним: <псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|открытые byte [] encryptColumnEncryptionKey (masterKeyPath строка, строка encryptionAlgorithm, plainTextColumnEncryptionKey byte [])|Шифрует ключ шифрования столбца с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Формат пути к ключу должен быть одним из следующих:**<br /><br /> Отпечаток: <отпечаток_сертификата><br /><br /> Псевдоним: <псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|открытые setName void (строковое имя)|Задает имя поставщика хранилища ключей.|
|открытые getName String)|Получает имя поставщика хранилища ключей.|
  
 **Класс SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Реализация поставщика хранилища ключей для хранилища ключей Azure. Этот класс позволяет использовать ключи, хранящиеся в хранилище ключей Azure в качестве главных ключей столбца.  
  
 Конструкторы  
  
|Название|Описание|  
|----------|-----------------|  
|открытый SQLServerColumnEncryptionAzureKeyVaultProvider (строка clientId, clientKey строка)|Поставщик хранилища ключей для хранилища ключей Azure.  Необходимо указать идентификатор и ключ запрашивает токен проверки подлинности клиента в хранилище ключей Azure.|  
  
 Методы  
  
|Название|Описание|  
|----------|-----------------|  
|открытые byte [] decryptColumnEncryptionKey (masterKeyPath строка, строка encryptionAlgorithm, encryptedColumnEncryptionKey byte [])|Расшифровывает указанное зашифрованное значение ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью указанного столбца ключа IDmaster ключа и с помощью указанного алгоритма. <br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|открытые byte [] encryptColumnEncryptionKey (masterKeyPath строка, строка encryptionAlgorithm, columnEncryptionKey byte [])|Шифрует ключ шифрования столбца с помощью главного ключа указанного столбца и с помощью указанного алгоритма. <br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|открытые setName void (строковое имя)|Задает имя поставщика хранилища ключей.|
|открытые getName String)|Получает имя поставщика хранилища ключей.|  
  
  
 **Интерфейс SQLServerKeyVaultAuthenticationCallback**  
  
 Этот интерфейс содержит один метод для проверки подлинности хранилища ключей Azure, которая должна быть реализована пользователем.  
  
 Методы  
  
|Название|Описание|  
|----------|-----------------|  
|открытый getAccessToken строки (строка центра, строкового ресурса, область строка);|Метод должен быть переопределен. Метод используется для получения доступа к токена в хранилище ключей Azure.|  
  
 **Класс SQLServerColumnEncryptionKeyStoreProvider**  
  
 Расширьте этот класс для реализации пользовательского поставщика хранилища ключей.  
  
|Название|Описание|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Базовый класс для всех поставщиков хранилища ключей. Настраиваемый поставщик должен наследовать от этого класса и переопределить свои функции-члены и затем зарегистрируйте его с помощью SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Методы  
  
|Название|Описание|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Метод базового класса для расшифровки указанного зашифрованного значения ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Метод базового класса для шифрования ключа шифрования столбца с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|
|открытый абстрактный void setName (строковое имя)|Задает имя поставщика хранилища ключей.|
|открытый абстрактный getName() строки|Получает имя поставщика хранилища ключей.|  
  
 Новые или перегруженные методы в **SQLServerPreparedStatement** класса  
  
|Название|Описание|  
|----------|-----------------|  
|открытые void setBigDecimal (int parameterIndex, BigDecimal x int точность, масштаб int)<br /><br /> открытые void setObject (int parameterIndex, объект x, int targetSqlType, целое число со знаком точность и масштаб int)<br /><br /> открытые void setObject (int parameterIndex, объект x, SQLType targetSqlType, целочисленный точность и масштаб целое число)<br /><br /> открытые void setTime (int parameterIndex, java.sql.Time x масштаб int)<br /><br /> открытые void setTimestamp (int parameterIndex, java.sql.Timestamp, int шкала x) <br />открытые void setDateTimeOffset (int parameterIndex, microsoft.sql.DateTimeOffset x масштаб int)|Эти методы являются перегруженными с точностью аргумент масштаба и/или для поддержки постоянного шифрования для определенных типов данных, где требуется точность и масштаб сведения.|  
|открытый setMoney void (int parameterIndex, BigDecimal x)<br /><br /> открытый setSmallMoney void (int parameterIndex, BigDecimal x)<br /><br /> открытый setUniqueIdentifier void (int parameterIndex, строка guid)<br /><br /> открытый setDateTime void (int parameterIndex, java.sql.Timestamp x)<br /><br /> открытый setSmallDateTime void (int parameterIndex, java.sql.Timestamp x)|Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание, что существующий метод setTimestamp() используется для отправки зашифрованных datetime2 столбца значений параметров. Для зашифрованных datetime и smalldatetime столбцы использовать новые методы setDateTime() и setSmallDateTime() соответственно.|  
|открытые окончательного void setBigDecimal (int parameterIndex, BigDecimal x int точность, масштаб int, boolean forceEncrypt)<br /><br /> setMoney последний открытый void (int parameterIndex, BigDecimal x логическое forceEncrypt)<br /><br /> setSmallMoney последний открытый void (int parameterIndex, BigDecimal x логическое forceEncrypt)<br /><br /> открытые окончательного void setBoolean (int parameterIndex, boolean x, логическое forceEncrypt)<br /><br /> открытые окончательного void setByte (int parameterIndex, byte x логическое forceEncrypt)<br /><br /> открытые окончательного void setBytes (int parameterIndex, x[] байтов, boolean forceEncrypt)<br /><br /> открытые окончательного void setUniqueIdentifier (int parameterIndex, строка guid, boolean forceEncrypt)<br /><br /> открытые окончательного void setDouble (int parameterIndex, double x, логическое forceEncrypt)<br /><br /> открытые окончательного void setFloat (int parameterIndex, число с плавающей запятой x, логическое forceEncrypt)<br /><br /> открытые окончательного void setInt (int parameterIndex, значения типа int, boolean forceEncrypt)<br /><br /> открытые окончательного void setLong (int parameterIndex, long x, логическое forceEncrypt)<br /><br /> открытые окончательного setObject (int parameterIndex, объект x, int targetSqlType, целое число со знаком точность, масштаб int, boolean forceEncrypt)<br /><br /> открытые окончательного void setObject (int parameterIndex, объект x, SQLType targetSqlType, целое число со знаком точность, масштаб целое число, логическое forceEncrypt)<br /><br /> открытые окончательного void setShort (int parameterIndex, короткое x, логическое forceEncrypt)<br /><br /> открытые окончательного void setString (int parameterIndex str строка, логическое forceEncrypt)<br /><br /> открытые окончательного void setNString (int parameterIndex, строковое значение, логическое forceEncrypt)<br /><br /> открытые окончательного setTime void (parameterIndex int, java.sql.Time x масштаб int логическое forceEncrypt)<br /><br /> открытые окончательного void setTimestamp (parameterIndex int, java.sql.Timestamp x масштаб int логическое forceEncrypt)<br /><br /> открытые окончательного void setDateTimeOffset (parameterIndex int, microsoft.sql.DateTimeOffset x масштаб int логическое forceEncrypt)<br /><br /> открытые окончательного void setDateTime (int parameterIndex, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытые окончательного void setSmallDateTime (int parameterIndex, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытые окончательного void setDate (parameterIndex int, java.sql.Date x java.util.Calendar cal логическое forceEncrypt)<br /><br /> открытые окончательного setTime void (parameterIndex int, java.sql.Time x java.util.Calendar cal логическое forceEncrypt)<br /><br /> открытые окончательного void setTimestamp (parameterIndex int, java.sql.Timestamp x java.util.Calendar cal логическое forceEncrypt)|Присваивает указанному параметру значение заданного java.<br /><br /> Если логическое forceEncrypt задано значение true, то запрос параметра будет устанавливать, только если столбец обозначение зашифрован и включено постоянное шифрование при соединении или в отчете.<br /><br /> Если логическое forceEncrypt имеет значение false, драйвер не будет устанавливать параметры шифрования.|  
  
 Новые или перегруженные методы в **SQLServerCallableStatement** класса  
  
|Название|Описание|  
|----------|-----------------|  
|открытые void registerOutParameter (int parameterIndex, int sqlType, int точность, масштаб int)<br /><br /> открытые void registerOutParameter (int parameterIndex, SQLType sqlType, int точность, масштаб int)<br /><br /> открытые void registerOutParameter (строка Имя_параметра, int sqlType, int точность, масштаб int)<br /><br /> открытые void registerOutParameter (строка Имя_параметра, SQLType sqlType, int точность, масштаб int)<br />открытые void setBigDecimal (строка Имя_параметра, BigDecimal bd, int точность, масштаб int)<br /><br /> открытые void setTime (строка Имя_параметра, java.sql.Time t, int масштаб)<br /><br /> открытые void setTimestamp (строка Имя_параметра, java.sql.Timestamp t, int масштаб)<br /><br /> открытые void setDateTimeOffset (строка Имя_параметра, microsoft.sql.DateTimeOffset t, int масштаб)<br/><br/>открытые окончательного void setObject (sCol строка, объект x, int targetSqlType, целое число со знаком точность и масштаб int)|Эти методы являются перегруженными с точностью аргумент масштаба и/или для поддержки постоянного шифрования для определенных типов данных, где требуется точность и масштаб сведения.|  
|открытый setDateTime void (строка Имя_параметра, java.sql.Timestamp x)<br /><br /> открытый setSmallDateTime void (строка Имя_параметра, java.sql.Timestamp x)<br /><br /> открытый setUniqueIdentifier void (Имя_параметра строка, строка guid)<br /><br /> открытый setMoney void (строка Имя_параметра, BigDecimal bd)<br /><br /> открытый setSmallMoney void (строка Имя_параметра, BigDecimal bd)<br/><br/>открытые getDateTime отметка времени (int index)<br/><br/>открытые getDateTime отметка времени (строка sCol)<br/><br/>открытые getDateTime отметка времени (int индекса, календарь cal)<br/><br/>открытый getSmallDateTime отметка времени (int index)<br/><br/>открытый getSmallDateTime отметка времени (строка sCol)<br/><br/>открытый getSmallDateTime отметка времени (int индекса, календарь cal)<br/><br/>открытый getSmallDateTime отметка времени (имя строки, календарь cal)<br/><br/>открытый BigDecimal getMoney (int index)<br/><br/>открытый BigDecimal getMoney (строка sCol)<br/><br/>открытый BigDecimal getSmallMoney (int index)<br/><br/>открытый BigDecimal getSmallMoney (строка sCol)|Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание, что существующий метод setTimestamp() используется для отправки зашифрованных datetime2 столбца значений параметров. Для зашифрованных datetime и smalldatetime столбцы использовать новые методы setDateTime() и setSmallDateTime() соответственно.|  
|открытые void setObject (строка Имя_параметра, Object o, int n, int m, логическое forceEncrypt)<br /><br /> открытые void setObject (Имя_параметра строка, объект obj, SQLType jdbcType, масштаба int, boolean forceEncrypt)<br /><br /> открытые void setDate (строка Имя_параметра, java.sql.Date x c календаря логическое forceEncrypt)<br /><br /> открытые void setTime (строка Имя_параметра, java.sql.Time t, масштаба int, boolean forceEncrypt)<br /><br /> открытые void setTime (строка Имя_параметра, java.sql.Time x c календаря логическое forceEncrypt)<br /><br /> открытый setDateTime void (строка Имя_параметра, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытые void setDateTimeOffset (строка Имя_параметра, microsoft.sql.DateTimeOffset t, масштаба int, boolean forceEncrypt)<br /><br /> открытый setSmallDateTime void (строка Имя_параметра, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытые void setTimestamp (строка Имя_параметра, java.sql.Timestamp t, int масштаба, логическое forceEncrypt)<br /><br /> открытые void setTimestamp (строка Имя_параметра, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый setUniqueIdentifier void (Имя_параметра строка, строка guid, boolean forceEncrypt)<br /><br /> открытые void setBytes (строка Имя_параметра, b byte [], логическое forceEncrypt)<br /><br /> открытые void setByte (строка Имя_параметра, байтов b, логическое forceEncrypt)<br /><br /> открытые void setString (Имя_параметра строки, s строка, логическое forceEncrypt)<br /><br /> открытые окончательного void setNString (Имя_параметра строка, строковое значение, логическое forceEncrypt)<br /><br /> открытый setMoney void (строка Имя_параметра, BigDecimal bd, логическое forceEncrypt)<br /><br /> открытый setSmallMoney void (строка Имя_параметра, BigDecimal bd, логическое forceEncrypt)<br /><br /> открытые void setBigDecimal (строка Имя_параметра, BigDecimal bd, точность int, int масштаба, логическое forceEncrypt)<br /><br /> открытые void setDouble (строка Имя_параметра double, d логическое forceEncrypt)<br /><br /> открытые void setFloat (Имя_параметра строку, число с плавающей запятой f, логическое forceEncrypt)<br /><br /> открытые void setInt (строка Имя_параметра, int i, логическое forceEncrypt)<br /><br /> открытые void setLong (строка Имя_параметра, долго l, логическое forceEncrypt)<br /><br /> открытые void setShort (строка Имя_параметра, short s, логическое forceEncrypt)<br /><br /> открытые void setBoolean (parameterNames строка, логическое значение b, логическое forceEncrypt)<br/><br/>открытые void setTimeStamp (строка sCol, java.sql.Timestamp x c календаря логическое forceEncrypt)|Присваивает указанному параметру значение заданного java.<br /><br /> Если логическое forceEncrypt задано значение true, то запрос параметра будет устанавливать, только если столбец обозначение зашифрован и включено постоянное шифрование при соединении или в отчете.<br /><br /> Если логическое forceEncrypt имеет значение false, драйвер не будет устанавливать параметры шифрования.|
 

 Новые или перегруженные методы в **SQLServerResultSet** класса  
  
|Название|Описание|  
|----------|-----------------|  
|Открытые строки getUniqueIdentifier (int columnIndex)<br/><br/>открытый getUniqueIdentifier строки (строка ColumnLabel состоит из)<br/><br/>   открытый java.sql.Timestamp getDateTime (int columnIndex) <br/><br/> открытый java.sql.Timestamp getDateTime (columnName строка)   <br/><br/> открытый java.sql.Timestamp getDateTime (int columnIndex, календарь cal)   <br/><br/>открытый java.sql.Timestamp getDateTime (строка colName, календарь cal)    <br/><br/>открытый java.sql.Timestamp getSmallDateTime (int columnIndex)    <br/><br/> открытый java.sql.Timestamp getSmallDateTime (columnName строка)   <br/><br/> открытый java.sql.Timestamp getSmallDateTime (int columnIndex, календарь cal)   <br/><br/> открытый java.sql.Timestamp getSmallDateTime (colName строки, календарь cal)   <br/><br/>  открытый BigDecimal getMoney (int columnIndex)  <br/><br/> открытый BigDecimal getMoney (columnName строка)   <br/><br/> открытый BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  открытый BigDecimal getSmallMoney (columnName строка)  <br/><br/>открытый updateMoney void (columnName строки, BigDecimal x)    <br/><br/>  открытый updateSmallMoney void (columnName строки, BigDecimal x)  <br/><br/>     открытый updateDateTime void (индекс int, java.sql.Timestamp x) <br/><br/> открытый updateSmallDateTime void (индекс int, java.sql.Timestamp x) |Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание, что существующий метод updateTimestamp() используется для обновления столбцов, зашифрованных datetime2. Для зашифрованных datetime и smalldatetime столбцы использовать новые методы updateDateTime() и updateSmallDateTime() соответственно.|
|открытые void updateBoolean (int index, логическое x, логическое forceEncrypt)  <br/><br/>  открытые void updateByte (int индекса, байтов x логическое forceEncrypt)  <br/><br/>  открытые void updateShort (int index, короткое x, логическое forceEncrypt)  <br/><br/> открытые void updateInt (индекс int, int x логическое forceEncrypt)   <br/><br/>  открытые void updateLong (индекс int, long x, логическое forceEncrypt)  <br/><br/> открытые void updateFloat (int index, число с плавающей запятой x, логическое forceEncrypt)   <br/><br/> открытые void updateDouble (int index, double x, логическое forceEncrypt)   <br/><br/> открытый updateMoney void (int index, BigDecimal x логическое forceEncrypt)   <br/><br/>  открытый updateMoney void (columnName строка BigDecimal x логическое forceEncrypt)  <br/><br/> открытый updateSmallMoney void (int index, BigDecimal x логическое forceEncrypt)   <br/><br/>  открытый updateSmallMoney void (columnName строка BigDecimal x логическое forceEncrypt)  <br/><br/> открытые void updateBigDecimal (int индекса, BigDecimal x точности целое число со знаком, масштаб целое число, логическое forceEncrypt)   <br/><br/>  открытые void updateString (int columnIndex, stringValue строка, логическое forceEncrypt)  <br/><br/>  открытые void updateNString (int columnIndex, nString строка, логическое forceEncrypt)  <br/><br/>  открытые void updateNString (ColumnLabel состоит из строки, nString строка, логическое forceEncrypt)  <br/><br/> открытые void updateBytes (int index, x[] байтов, boolean forceEncrypt)   <br/><br/>  открытые void updateDate (индекс int, java.sql.Date x логическое forceEncrypt)  <br/><br/> открытые void updateTime (индекс int, java.sql.Time x масштаб целое число, логическое forceEncrypt)   <br/><br/> открытые void updateTimestamp (индекс int, java.sql.Timestamp x масштаб int логическое forceEncrypt)   <br/><br/> открытый updateDateTime void (индекс int, java.sql.Timestamp x масштаб целое число, логическое forceEncrypt)   <br/><br/> открытый updateSmallDateTime void (индекс int, java.sql.Timestamp x масштаб целое число, логическое forceEncrypt)   <br/><br/>  открытый метод updateDateTimeOffset void (индекс int, microsoft.sql.DateTimeOffset x масштаб целое число, логическое forceEncrypt)  <br/><br/> открытый updateUniqueIdentifier void (int индекс, строки x логическое forceEncrypt)    <br/><br/>  открытые void updateObject (int индекса, объект x, int точность, масштаб int, boolean forceEncrypt)  <br/><br/>  открытые void updateObject (int индекса, объект obj, SQLType targetSqlType, int шкалы, логическое forceEncrypt)  <br/><br/> открытые void updateBoolean (columnName строка, логическое x, логическое forceEncrypt)    <br/><br/>  открытые void updateByte (columnName строки, байтов x логическое forceEncrypt)  <br/><br/>  открытые void updateShort (columnName строки, короткое x, логическое forceEncrypt)  <br/><br/> открытые void updateInt (columnName строки, int x логическое forceEncrypt)   <br/><br/>   открытые void updateLong (columnName строки, долго x, логическое forceEncrypt) <br/><br/>  открытые void updateFloat (columnName строку, число с плавающей запятой x, логическое forceEncrypt)  <br/><br/>  открытые void updateDouble (columnName строки, double x, логическое forceEncrypt)  <br/><br/> открытые void updateBigDecimal (columnName строка BigDecimal x логическое forceEncrypt)   <br/><br/>  открытые void updateBigDecimal (columnName строки, BigDecimal x точности целое число со знаком, масштаб целое число, логическое forceEncrypt)  <br/><br/> открытые void updateString (columnName строка, строка x логическое forceEncrypt)   <br/><br/>  открытые void updateBytes (columnName строки, x[] байтов, boolean forceEncrypt)  <br/><br/> открытые void updateDate (columnName строки, java.sql.Date x логическое forceEncrypt)   <br/><br/>  открытые void updateTime (columnName строки, java.sql.Time x масштаб int логическое forceEncrypt)  <br/><br/>  открытые void updateTimestamp (columnName строки, java.sql.Timestamp x масштаб int логическое forceEncrypt)  <br/><br/> открытый updateDateTime void (columnName строки, java.sql.Timestamp x масштаб int логическое forceEncrypt)   <br/><br/>  открытый updateSmallDateTime void (columnName строки, java.sql.Timestamp x масштаб int логическое forceEncrypt)  <br/><br/>  открытый метод updateDateTimeOffset void (columnName строки, microsoft.sql.DateTimeOffset x масштаб int логическое forceEncrypt)  <br/><br/>  открытый updateUniqueIdentifier void (columnName строка, строка x логическое forceEncrypt)<br/><br/>открытые void updateObject (columnName строка, объект x, int точность, масштаб int, boolean forceEncrypt)<br/><br/>открытые void updateObject (columnName строка, объект obj, SQLType targetSqlType, масштаба int, boolean forceEncrypt)|Обновите указанный столбец к значению данного java.<br/><br/>Если логическое forceEncrypt задано значение true, столбец будет устанавливать, только если он зашифрован и постоянное шифрование включено при соединении или на инструкции.<br/><br/>Если логическое forceEncrypt имеет значение false, драйвер не будет устанавливать параметры шифрования.|

  
Новые типы в **microsoft.sql.Types** класса
|Название|Описание|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Использовать эти типы в качестве целевых типов SQL при отправке значения параметра **зашифрованные** datetime, smalldatetime, money, smallmoney, с помощью методов setObject()/updateObject() API столбцы уникального идентификатора.|  
  
  
 **Перечисление SQLServerStatementColumnEncryptionSetting**  
  
 Указывает, отправленных и полученных при чтении и записи зашифрованных столбцов данных. В зависимости от конкретного запроса влияние на производительность может снизиться при обходе драйвер постоянного шифрования обработки при использовании незашифрованных столбцов. Обратите внимание, что эти параметры нельзя использовать для обхода шифрования и получения доступа к данным в виде обычного текста.  
  
 **Синтаксис**  
  
```  
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Члены**  
  
|Название|Описание|  
|----------|-----------------|  
|UseConnectionSetting|Указывает, что команда должна использовать по умолчанию параметр всегда зашифрованы в строке подключения.|  
|Включено|Включает постоянное шифрование для запроса.|  
|ResultSetOnly|Указывает, что только результаты выполнения команды должен обрабатываться всегда зашифрованы в драйвере. Это значение следует используйте, если команда не имеет параметров, требующих шифрования.|  
|Выключено|Отключает постоянное шифрование для запроса.|  
  
 Настройка уровня инструкции для AE добавляются для класса SQLServerConnection и SQLServerConnectionPoolProxy класса. Следующие методы в этих классов являются перегруженными с помощью нового параметра.  
  
|Название|Описание|  
|----------|-----------------|  
|открытый оператор createStatement (int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект инструкции, будут создаваться объекты результирующего набора с указанным параметром типа, параллелизма, удержание и столбец шифрования.|  
|открытый CallableStatement prepareCall (строка sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|Создает объект CallableStatement с параметром шифрования данного столбца, который создает объекты результирующего набора с заданным типом, параллелизма и возможностью сохранения.|  
|открытый PreparedStatement prepareStatement (строка sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметр шифрования данного столбца, с возможностью получения автоматически сформированных ключей.|  
|открытый PreparedStatement prepareStatement (строка sql, строка [] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметром шифрования данного столбца, который создает результирующий набор объектов, содержащих имя заданного столбца.|  
|открытый PreparedStatement prepareStatement (строка sql columnIndexes int [], SQLServerStatementColumnEncryptionSetting stmtColEncSetting|Создает объект PreparedStatement с параметром шифрования данного столбца, который создает объекты результирующего набора с индексами данного столбца.|  
|открытый PreparedStatement prepareStatement (строка sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметром шифрования данного столбца, который создает объекты результирующего набора с заданным типом, параллелизма и возможностью сохранения.|  
  
> [!NOTE]  
>  Если постоянное шифрование отключено для запроса и запрос содержит параметры, которые должны быть зашифрованных (параметры, соответствующие зашифрованных столбцов), запрос завершится ошибкой.  
>   
>  Если постоянное шифрование отключено для запроса и запрос возвращает результаты из зашифрованных столбцов, запрос будет возвращать зашифрованные значения. Зашифрованные значения будут иметь тип данных varbinary.  
  
 ## <a name="see-also"></a>См. также  
 [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

