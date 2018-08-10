---
title: Справочник по API Always Encrypted для драйвера JDBC | Документы Майкрософт
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b305c9e42f1eb7dffec8bd00204723a142a6b2e
ms.sourcegitcommit: 50144371c9ee924e5c0b4b9d3d4860f531c27426
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39582170"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Справочник по API Always Encrypted для драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Функция Always Encrypted позволяет клиентам шифровать конфиденциальные данные в клиентских приложениях, не раскрывая ключи шифрования для SQL Server. Драйвер с поддержкой Always Encrypted, установленный на клиентском компьютере, реализует эту функцию за счет автоматического шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер шифрует данные из конфиденциальных столбцов перед их передачей в SQL Server и автоматически переписывает запросы, чтобы сохранить семантику приложения. Аналогичным образом драйвер прозрачно расшифровывает данные, хранящиеся в столбцах зашифрованной базы данных, которые содержатся в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted поддерживается только Microsoft JDBC Driver 6.0 или более поздней версии для SQL Server с SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Справочник по API Always Encrypted
 
 Существует несколько дополнений и изменений для API драйвера JDBC для использования в клиентских приложениях, использующих функцию Always Encrypted.  
  
 **Класс SQLServerConnection**  
  
|Имя|Описание|  
|----------|-----------------|  
|Новое ключевое слово строки подключения:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled включает функцию Always Encrypted для подключения, а columnEncryptionSetting=Disabled отключает ее. Допустимыми являются значения Enabled/Disabled. По умолчанию установлено значение Disabled.|  
|Новые методы:<br /><br /> открытый статический void setColumnEncryptionTrustedMasterKeyPaths (Map < String, список\<строка >> trustedKeyPaths)<br /><br /> открытый статический updateColumnEncryptionTrustedMasterKeyPaths void (список строка сервера\<строка > trustedKeyPaths)<br /><br /> открытый статический void removeColumnEncryptionTrustedMasterKeyPaths (String server)|Позволяет задавать, обновлять и удалять список доверенных путей ключа для сервера базы данных. Если при обработке запроса приложения драйвер получает путь ключа, которого нет в списке, запрос завершается с ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих отправку скомпрометированным SQL Server фиктивных путей ключа, которые могут привести к утечке учетных данных хранилища ключей.|  
|Новый метод:<br /><br /> public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()|Возвращает список доверенных путей ключа для сервера базы данных.|  
|Новый метод:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)|Позволяет регистрировать пользовательские поставщики хранилища ключей. Это словарь, сопоставляющий имена поставщиков хранилища ключей с реализациями поставщиков хранилища ключей.<br /><br /> Для использования хранилища ключей виртуальной машины Java необходимо создать экземпляр объекта SQLServerColumnEncryptionJVMKeyStoreProvider с помощью учетных данных хранилища ключей виртуальной машины Java и зарегистрировать его с помощью драйвера. Имя этого поставщика должно иметь вид MSSQL_JVM_KEYSTORE.<br /><br /> Чтобы использовать хранилище Azure Key Vault, необходимо создать экземпляр объекта SQLServerColumnEncryptionAzureKeyStoreProvider и зарегистрируйте его с помощью драйвера. Имя для этого поставщика должно быть «AZURE_KEY_VAULT».|
|public final boolean getSendTimeAsDatetime()|Возвращает значение свойства соединения sendTimeAsDatetime.|
|открытый void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)|Изменяет свойства sendTimeAsDatetime соединения.|

 **Класс SQLServerConnectionPoolProxy**
|Имя|Описание|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|Возвращает значение свойства соединения sendTimeAsDatetime.|
|открытый void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)|Изменяет свойства sendTimeAsDatetime соединения.|
     
  
 **Класс SQLServerDataSource**  
  
|Имя|Описание|  
|----------|-----------------|  
|public void setColumnEncryptionSetting(String columnEncryptionSetting)|Включает или отключает функцию Always Encrypted для объекта источника данных.<br /><br /> По умолчанию установлено значение Disabled.|  
|открытый getColumnEncryptionSetting() строки|Получает параметр функции Always Encrypted для объекта источника данных.|
|открытый void setKeyStoreAuthentication (строка keyStoreAuthentication)|Задает имя, идентифицирующее хранилище ключей. Поддерживается только значение **JavaKeyStorePassword** для идентификации Store ключ Java.<br/><br/>Значение по умолчанию — NULL.|
|открытый getKeyStoreAuthentication() строки|Получает значение параметра "keyStoreAuthentication" для объекта источника данных.|
|открытый void setKeyStoreSecret (строка keyStoreSecret)|Задает пароль для хранилища ключей Java. Пароль для хранилища ключей и ключ должны совпадать. Обратите внимание, что keyStoreAuthentication следует передавать в **JavaKeyStorePassword**.|
|открытый void setKeyStoreLocation (строка keyStoreLocation)|Задает расположение, включая имя файла для Java хранилища ключей. Обратите внимание, что keyStoreAuthentication следует передавать в **JavaKeyStorePassword**.|
|открытый getKeyStoreLocation() строки|Извлекает keyStoreLocation для Store ключ Java.|
  
 **Класс SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Реализация поставщика хранилища ключей для хранилища ключей Java. Этот класс позволяет использовать сертификаты, находящиеся в хранилище ключей Java, в качестве главных ключей столбца.  
  
 Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый SQLServerColumnEncryptionJavaKeyStoreProvider (строка keyStoreLocation, keyStoreSecret char [])|Поставщик хранилища ключей для Store ключ Java.|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Расшифровывает указанное зашифрованное значение ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Путь ключа должен иметь один из следующих форматов.**<br /><br /> Отпечаток: <отпечаток_сертификата><br /><br /> Псевдоним: <псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. метода decryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)|Шифрует ключ шифрования столбца с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Путь ключа должен иметь один из следующих форматов.**<br /><br /> Отпечаток: <отпечаток_сертификата><br /><br /> Псевдоним: <псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (строка, String, Byte[]).) программы|  
|открытый void setName (имя строки)|Задает имя поставщика хранилища ключей.|
|public String getName ()|Получает имя поставщика хранилища ключей.|
  
 **Класс SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Реализация поставщика хранилища ключей для Azure Key Vault. Этот класс позволяет использовать ключи, хранящиеся в хранилище ключей Azure в качестве главных ключей столбца.  
  
 Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый SQLServerColumnEncryptionAzureKeyVaultProvider (строка clientId, clientKey строка)|Поставщик хранилища ключей для хранилища ключей Azure.  Необходимо указать идентификатор и ключ клиента, запрашивающего маркер для проверки подлинности в хранилище ключей Azure.|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
| public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey) | Decryptes ключ шифрования зашифрованного столбца (CEK). Этот расшифровки выполняется алгоритм шифрования RSA, который использует асимметричный ключ, указанный путь к главному ключу.<br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. метода decryptColumnEncryptionKey (строка, String, Byte[]).) программы |  
| public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey) | Шифрует ключ шифрования столбца, передав главный ключ столбца, указанного для указанного алгоритма.<br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (строка, String, Byte[]).) программы |  
|открытый void setName (имя строки)|Задает имя поставщика хранилища ключей.|
|public String getName ()|Получает имя поставщика хранилища ключей.|  
  
  
 **Интерфейс SQLServerKeyVaultAuthenticationCallback**  
  
 Этот интерфейс содержит один метод для проверки подлинности Azure Key Vault, что должна быть реализована пользователем.  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый строка getaccesstoken используется следующий (строка authority, строковый ресурс, область строку);|Метод должен быть переопределен. Метод позволяет получить маркер доступа для хранилища ключей Azure.|  
  
 **Класс SQLServerColumnEncryptionKeyStoreProvider**  
  
 Расширьте этот класс для реализации пользовательского поставщика хранилища ключей.  
  
|Имя|Описание|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Базовый класс для всех поставщиков хранилища ключей. Пользовательский поставщик должен наследовать от этого класса и переопределять его функции-члены, а затем регистрировать его с помощью SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Метод базового класса для расшифровки указанного зашифрованного значения ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Метод базового класса для шифрования ключа шифрования столбца с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|
|открытый абстрактный void setName (имя строки)|Задает имя поставщика хранилища ключей.|
|открытый абстрактный getName() строки|Получает имя поставщика хранилища ключей.|  
  
 Новые или перегруженные методы в **SQLServerPreparedStatement** класса  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый void setBigDecimal (int parameterIndex, BigDecimal x, int точность, масштаб int)<br /><br /> открытый void setObject (int parameterIndex, объект x, int targetSqlType, целое число точность, масштаб int)<br /><br /> открытый void setObject (int parameterIndex, объект x, SQLType targetSqlType, целое число точность, масштаб целое число)<br /><br /> открытый void setTime (int parameterIndex, java.sql.Time, int шкала x)<br /><br /> открытый void setTimestamp (int parameterIndex, java.sql.Timestamp, int шкала x) <br />открытый void setDateTimeOffset (int parameterIndex, microsoft.sql.DateTimeOffset x масштабирования int)|Эти методы являются перегруженными с точностью аргумент масштаба и/или для поддержки постоянного шифрования для определенных типов данных, которые требуется точность и сведения о масштабе.|  
|открытый setMoney void (int parameterIndex, BigDecimal x)<br /><br /> открытый setSmallMoney void (int parameterIndex, BigDecimal x)<br /><br /> открытый void setUniqueIdentifier (int parameterIndex, строка guid)<br /><br /> открытый setDateTime void (int parameterIndex, java.sql.Timestamp x)<br /><br /> открытый setSmallDateTime void (int parameterIndex, java.sql.Timestamp x)|Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание на то, что существующий метод setTimestamp() используется для отправки значения параметров в столбце зашифрованных datetime2. Для зашифрованных типов datetime и smalldatetime столбцы использовать новые методы setDateTime() и setSmallDateTime() соответственно.|  
|открытый окончательный void setBigDecimal (int parameterIndex, BigDecimal x, int точность, масштаб int, boolean forceEncrypt)<br /><br /> открытый окончательный void setMoney (int parameterIndex, BigDecimal x логическое forceEncrypt)<br /><br /> открытый окончательный void setSmallMoney (int parameterIndex, BigDecimal x логическое forceEncrypt)<br /><br /> открытый окончательный void setBoolean (int parameterIndex, boolean x, логическое forceEncrypt)<br /><br /> открытый окончательный void setByte (int parameterIndex, byte x логическое forceEncrypt)<br /><br /> открытый окончательный void setBytes (int parameterIndex, byte x[], логическое forceEncrypt)<br /><br /> открытый окончательный void setUniqueIdentifier (int parameterIndex, guid строку, логическое forceEncrypt)<br /><br /> открытый окончательный void setDouble (int parameterIndex, double x, логическое forceEncrypt)<br /><br /> открытый окончательный void setFloat (int parameterIndex, float x, логическое forceEncrypt)<br /><br /> открытый окончательный void setInt (int parameterIndex, значение типа int, boolean forceEncrypt)<br /><br /> открытый окончательный void setLong (int parameterIndex, long x, логическое forceEncrypt)<br /><br /> открытый окончательный setObject (int parameterIndex, объект x, int targetSqlType, целое число точности и масштаба int, boolean forceEncrypt)<br /><br /> открытый окончательный void setObject (int parameterIndex, объект x, SQLType targetSqlType, целое число точности и масштаба целое число, логическое forceEncrypt)<br /><br /> открытый окончательный void setShort (int parameterIndex, короткие x, логическое forceEncrypt)<br /><br /> открытый окончательный void setString (forceEncrypt логическое parameterIndex, строка str, int)<br /><br /> открытый окончательный void setNString (int parameterIndex, строковое значение, логическое forceEncrypt)<br /><br /> открытый окончательный void setTime (parameterIndex int, java.sql.Time, int шкала x, логическое forceEncrypt)<br /><br /> открытый окончательный void setTimestamp (parameterIndex int, java.sql.Timestamp, int шкала x, логическое forceEncrypt)<br /><br /> открытый окончательный void setDateTimeOffset (parameterIndex int, microsoft.sql.DateTimeOffset x масштабирования int логическое forceEncrypt)<br /><br /> открытый окончательный void setDateTime (int parameterIndex, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый окончательный void setSmallDateTime (int parameterIndex, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый окончательный void setDate (parameterIndex int, java.sql.Date x, java.util.Calendar cal, логическое forceEncrypt)<br /><br /> открытый окончательный void setTime (parameterIndex int, java.sql.Time x, java.util.Calendar cal, логическое forceEncrypt)<br /><br /> открытый окончательный void setTimestamp (parameterIndex int, java.sql.Timestamp x, java.util.Calendar cal, логическое forceEncrypt)|Задает указанному параметру заданное значение типа Java.<br /><br /> Если логическое forceEncrypt имеет значение true, в запросе параметр будет устанавливать, только если обозначение столбец зашифрован и постоянное шифрование включено для соединения или в отчете.<br /><br /> Если логическое forceEncrypt имеет значение false, драйвер не принудительное шифрование параметров.|  
  
 Новые или перегруженные методы в **SQLServerCallableStatement** класса  
  
|Имя|Описание|  
|----------|-----------------|  
|public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />открытый void setBigDecimal (строка parameterName, BigDecimal bd, int точности и масштаба int)<br /><br /> открытый void setTime (строка parameterName, java.sql.Time t, int масштаб)<br /><br /> открытый void setTimestamp (строка parameterName, java.sql.Timestamp t, int масштаб)<br /><br /> открытый void setDateTimeOffset (строка parameterName, microsoft.sql.DateTimeOffset t, int масштаб)<br/><br/>открытый окончательный void setObject (sCol строка, объект x, int targetSqlType, целое число точность, масштаб int)|Эти методы являются перегруженными с точностью аргумент масштаба и/или для поддержки постоянного шифрования для определенных типов данных, которые требуется точность и сведения о масштабе.|  
|открытый setDateTime void (строка parameterName, java.sql.Timestamp x)<br /><br /> открытый setSmallDateTime void (строка parameterName, java.sql.Timestamp x)<br /><br /> открытый void setUniqueIdentifier (parameterName строка, строка guid)<br /><br /> открытый void setMoney (строка parameterName, BigDecimal bd)<br /><br /> открытый void setSmallMoney (строка parameterName, BigDecimal bd)<br/><br/>открытый getDateTime Timestamp (int index)<br/><br/>открытый getDateTime отметки времени (строка sCol)<br/><br/>открытый getDateTime Timestamp (int индекса, cal календаря)<br/><br/>открытый getSmallDateTime Timestamp (int index)<br/><br/>открытый getSmallDateTime отметки времени (строка sCol)<br/><br/>открытый getSmallDateTime Timestamp (int индекса, cal календаря)<br/><br/>открытый getSmallDateTime Timestamp (имя строки, cal календаря)<br/><br/>открытый BigDecimal getMoney (int index)<br/><br/>открытый BigDecimal getMoney (строка sCol)<br/><br/>открытый BigDecimal getSmallMoney (int index)<br/><br/>открытый BigDecimal getSmallMoney (строка sCol)|Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание на то, что существующий метод setTimestamp() используется для отправки значения параметров в столбце зашифрованных datetime2. Для зашифрованных типов datetime и smalldatetime столбцы использовать новые методы setDateTime() и setSmallDateTime() соответственно.|  
|открытый void setObject (строка parameterName, Object o, int n, int m, логическое forceEncrypt)<br /><br /> открытый void setObject (parameterName строка, объект obj, SQLType jdbcType, int масштаба, логическое forceEncrypt)<br /><br /> открытый void setDate (строка parameterName, java.sql.Date x c календаря, логическое forceEncrypt)<br /><br /> открытый void setTime (parameterName строки, java.sql.Time t, масштабирование int, boolean forceEncrypt)<br /><br /> открытый void setTime (строка parameterName, java.sql.Time x c календаря, логическое forceEncrypt)<br /><br /> открытый void setDateTime (строка parameterName, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый void setDateTimeOffset (parameterName строки, microsoft.sql.DateTimeOffset t, масштабирование int, boolean forceEncrypt)<br /><br /> открытый void setSmallDateTime (строка parameterName, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый void setTimestamp (строка parameterName, java.sql.Timestamp t, int масштаба, логическое forceEncrypt)<br /><br /> открытый void setTimestamp (строка parameterName, java.sql.Timestamp x логическое forceEncrypt)<br /><br /> открытый void setUniqueIdentifier (parameterName строка, строка guid, boolean forceEncrypt)<br /><br /> открытый void setBytes (parameterName строки, byte [] b, логическое forceEncrypt)<br /><br /> открытый void setByte (строка parameterName, байтов b, логическое forceEncrypt)<br /><br /> открытый void setString (parameterName строки, s, строка, логическое forceEncrypt)<br /><br /> открытый окончательный void setNString (parameterName строка, строковое значение, логическое forceEncrypt)<br /><br /> открытый void setMoney (строка parameterName, BigDecimal bd, логическое forceEncrypt)<br /><br /> открытый void setSmallMoney (строка parameterName, BigDecimal bd, логическое forceEncrypt)<br /><br /> открытый void setBigDecimal (строка parameterName, BigDecimal bd, точность int, int масштаба, логическое forceEncrypt)<br /><br /> открытый void setDouble (строка parameterName, double d, логическое forceEncrypt)<br /><br /> открытый void setFloat (parameterName строка, число с плавающей запятой f, логическое forceEncrypt)<br /><br /> открытый void setInt (строка parameterName, int i, логическое forceEncrypt)<br /><br /> открытый void setLong (parameterName строка, длину l и логическое forceEncrypt)<br /><br /> открытый void setShort (строка parameterName, short s, логическое forceEncrypt)<br /><br /> открытый void setBoolean (parameterNames строка, логическое значение b, логическое forceEncrypt)<br/><br/>открытый void setTimeStamp (строка sCol, java.sql.Timestamp x c календаря логическое forceEncrypt)|Задает указанному параметру заданное значение типа Java.<br /><br /> Если логическое forceEncrypt имеет значение true, в запросе параметр будет устанавливать, только если обозначение столбец зашифрован и постоянное шифрование включено для соединения или в отчете.<br /><br /> Если логическое forceEncrypt имеет значение false, драйвер не принудительное шифрование параметров.|
 

 Новые или перегруженные методы в **SQLServerResultSet** класса  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый getUniqueIdentifier строку (int columnIndex)<br/><br/>открытый getUniqueIdentifier строку (строку ColumnLabel состоит из)<br/><br/>   открытый java.sql.Timestamp getDateTime (int columnIndex) <br/><br/> открытый java.sql.Timestamp getDateTime (columnName строка)   <br/><br/> открытый java.sql.Timestamp getDateTime (int columnIndex, cal календаря)   <br/><br/>открытый java.sql.Timestamp getDateTime (строка colName, cal календаря)    <br/><br/>открытый java.sql.Timestamp getSmallDateTime (int columnIndex)    <br/><br/> открытый java.sql.Timestamp getSmallDateTime (columnName строка)   <br/><br/> открытый java.sql.Timestamp getSmallDateTime (int columnIndex, cal календаря)   <br/><br/> открытый java.sql.Timestamp getSmallDateTime (строка colName, cal календаря)   <br/><br/>  открытый BigDecimal getMoney (int columnIndex)  <br/><br/> открытый BigDecimal getMoney (columnName строка)   <br/><br/> открытый BigDecimal getSmallMoney (int columnIndex)   <br/><br/>  открытый BigDecimal getSmallMoney (columnName строка)  <br/><br/>открытый updateMoney void (columnName строки, BigDecimal x)    <br/><br/>  открытый updateSmallMoney void (columnName строки, BigDecimal x)  <br/><br/>     открытый updateDateTime void (индекс int, java.sql.Timestamp x) <br/><br/> открытый updateSmallDateTime void (индекс int, java.sql.Timestamp x) |Эти методы добавляются для поддержки постоянного шифрования для данных типов money, smallmoney, uniqueidentifier, datetime и smalldatetime. <br/><br/>Обратите внимание на то, что существующий метод updateTimestamp() используется для обновления столбцов, зашифрованных datetime2. Для зашифрованных типов datetime и smalldatetime столбцы использовать новые методы updateDateTime() и updateSmallDateTime() соответственно.|
|открытый void updateBoolean (int index, логическое x, логическое forceEncrypt)  <br/><br/>  открытый void updateByte (int индекса, байтов x логическое forceEncrypt)  <br/><br/>  открытый void updateShort (int index, короткие x, логическое forceEncrypt)  <br/><br/> открытый void updateInt (индекс int, int x логическое forceEncrypt)   <br/><br/>  открытый void updateLong (int index, длительно x, логическое forceEncrypt)  <br/><br/> открытый void updateFloat (int index, число с плавающей запятой x, логическое forceEncrypt)   <br/><br/> открытый void updateDouble (int index, double x, логическое forceEncrypt)   <br/><br/> открытый void updateMoney (int index, BigDecimal x логическое forceEncrypt)   <br/><br/>  открытый void updateMoney (строка columnName, BigDecimal x логическое forceEncrypt)  <br/><br/> открытый void updateSmallMoney (int index, BigDecimal x логическое forceEncrypt)   <br/><br/>  открытый void updateSmallMoney (строка columnName, BigDecimal x логическое forceEncrypt)  <br/><br/> открытый void updateBigDecimal (int индекса, BigDecimal x точности целое число, масштаб целое число, логическое forceEncrypt)   <br/><br/>  открытый void updateString (int columnIndex, stringValue строка, логическое forceEncrypt)  <br/><br/>  открытый void updateNString (int columnIndex, nString строка, логическое forceEncrypt)  <br/><br/>  открытый void updateNString (ColumnLabel состоит из строки, nString строка, логическое forceEncrypt)  <br/><br/> открытый void updateBytes (int index, x[] байтов, boolean forceEncrypt)   <br/><br/>  открытый void updateDate (индекс int, java.sql.Date x логическое forceEncrypt)  <br/><br/> открытый void updateTime (индекс int, java.sql.Time x масштабирования целое число, логическое forceEncrypt)   <br/><br/> открытый void updateTimestamp (индекс int, java.sql.Timestamp, int шкала x, логическое forceEncrypt)   <br/><br/> открытый updateDateTime void (индекс int, java.sql.Timestamp x масштабирования целое число, логическое forceEncrypt)   <br/><br/> открытый updateSmallDateTime void (индекс int, java.sql.Timestamp x масштабирования целое число, логическое forceEncrypt)   <br/><br/>  открытый метод updateDateTimeOffset void (индекс int, microsoft.sql.DateTimeOffset x масштабирования целое число, логическое forceEncrypt)  <br/><br/> открытый void updateUniqueIdentifier (int index, строка x, логическое forceEncrypt)    <br/><br/>  открытый void updateObject (int индекса, объекта x, int точность, масштаб int, boolean forceEncrypt)  <br/><br/>  открытый void updateObject (int индекса, объект obj, SQLType targetSqlType, масштаба int, boolean forceEncrypt)  <br/><br/> открытый void updateBoolean (columnName строка, логическое x, логическое forceEncrypt)    <br/><br/>  открытый void updateByte (columnName строки, байтов x логическое forceEncrypt)  <br/><br/>  открытый void updateShort (columnName строки, короткие x, логическое forceEncrypt)  <br/><br/> открытый void updateInt (columnName строки, int x логическое forceEncrypt)   <br/><br/>   открытый void updateLong (columnName строка, длину x и логическое forceEncrypt) <br/><br/>  открытый void updateFloat (columnName строка, число с плавающей запятой x, логическое forceEncrypt)  <br/><br/>  открытый void updateDouble (columnName строки, double x, логическое forceEncrypt)  <br/><br/> открытый void updateBigDecimal (строка columnName, BigDecimal x логическое forceEncrypt)   <br/><br/>  открытый void updateBigDecimal (columnName строки, BigDecimal x точности целое число, масштаб целое число, логическое forceEncrypt)  <br/><br/> открытый void updateString (columnName строка, строка x, логическое forceEncrypt)   <br/><br/>  открытый void updateBytes (columnName строки, x[] байтов, boolean forceEncrypt)  <br/><br/> открытый void updateDate (columnName строки, java.sql.Date x логическое forceEncrypt)   <br/><br/>  открытый void updateTime (columnName строки, java.sql.Time, int шкала x, логическое forceEncrypt)  <br/><br/>  открытый void updateTimestamp (columnName строки, java.sql.Timestamp, int шкала x, логическое forceEncrypt)  <br/><br/> открытый updateDateTime void (columnName строки, java.sql.Timestamp, int шкала x, логическое forceEncrypt)   <br/><br/>  открытый updateSmallDateTime void (columnName строки, java.sql.Timestamp, int шкала x, логическое forceEncrypt)  <br/><br/>  открытый метод updateDateTimeOffset void (columnName строки, microsoft.sql.DateTimeOffset x масштабирования int, boolean forceEncrypt)  <br/><br/>  открытый void updateUniqueIdentifier (columnName строка, строка x, логическое forceEncrypt)<br/><br/>открытый void updateObject (columnName строка, объект x, int точность, масштаб int, boolean forceEncrypt)<br/><br/>открытый void updateObject (columnName строка, объект obj, SQLType targetSqlType, масштаба int, boolean forceEncrypt)|Обновите указанный столбец к значению заданного java.<br/><br/>Если задано значение forceEncrypt логическое значение равно true, столбец будет устанавливать, только если он зашифрован и постоянное шифрование включено для соединения или в отчете.<br/><br/>Если логическое forceEncrypt имеет значение false, драйвер не принудительное шифрование параметров.|

  
Новые типы в **microsoft.sql.Types** класса
|Имя|Описание|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Использовать эти типы в качестве целевых типов SQL, при отправке значения параметра **зашифрованных** datetime, smalldatetime, money, smallmoney, столбцы уникального идентификатора, с помощью методов setObject()/updateObject() API.|  
  
  
 **SQLServerStatementColumnEncryptionSetting Enum**  
  
 Указывает, каким образом данные будут отправлять и получать при чтении и записи зашифрованных столбцов. В зависимости от конкретного запроса влияние на производительность может снизиться при обходе Always Encrypted драйвер обработки при использовании незашифрованных столбцов. Обратите внимание на то, что эти параметры не может использоваться для обхода шифрования и получить доступ к данным в виде обычного текста.  
  
 **Синтаксис**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Члены**  
  
|Имя|Описание|  
|----------|-----------------|  
|UseConnectionSetting|Указывает, что команда должна использовать по умолчанию параметра Always Encrypted в строке подключения.|  
|Активировано|Обеспечивает постоянное шифрование для запроса.|  
|ResultSetOnly|Указывает, что только результаты выполнения команды должны обрабатываться подпрограммой Always Encrypted в драйвере. Это значение используется в том случае, если команда не имеет параметров, требующих шифрования.|  
|Выключено|Отключает Always Encrypted для запроса.|  
  
 Параметр уровня инструкции для AE добавляется в класс SQLServerConnection и к классу SQLServerConnectionPoolProxy. Следующие методы в эти классы являются перегруженными с помощью нового параметра.  
  
|Имя|Описание|  
|----------|-----------------|  
|открытый оператор createStatement (int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект оператор, который будет создавать объекты результирующего набора с заданным типом, параллелизма, удержание и параметр шифрования столбца.|  
|открытый CallableStatement prepareCall (строка sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|Создает объект CallableStatement с параметром шифрования данного столбца, который будет создавать объекты результирующего набора с заданным типом, параллелизма и возможностью сохранения.|  
|открытый prepareStatement PreparedStatement (строка sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметром шифрования данного столбца, с возможностью получения автоматически сформированных ключей.|  
|открытый prepareStatement PreparedStatement (строка sql, строка [] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметром шифрования данного столбца, который создаст объектов ResultSet с именами данного столбца.|  
|открытый prepareStatement PreparedStatement (строка sql, columnIndexes int [], SQLServerStatementColumnEncryptionSetting stmtColEncSetting программы|Создает объект PreparedStatement с параметром шифрования данного столбца, который создаст объектов ResultSet с индексами данного столбца.|  
|открытый prepareStatement PreparedStatement (строка sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Создает объект PreparedStatement с параметром шифрования данного столбца, который будет создавать объекты результирующего набора с заданным типом, параллелизма и возможностью сохранения.|  
  
> [!NOTE]  
>  Если постоянное шифрование отключено для запроса и запрос содержит параметры, которые должны быть зашифрованные (параметры, которые соответствуют зашифрованным столбцам), запрос завершится ошибкой.  
>   
>  Если постоянное шифрование отключено для запроса и запрос возвращает результаты из зашифрованных столбцов, запрос будет возвращать зашифрованные значения. Зашифрованные значения будут иметь тип данных varbinary.  
  
 ## <a name="see-also"></a>См. также:  
 [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

