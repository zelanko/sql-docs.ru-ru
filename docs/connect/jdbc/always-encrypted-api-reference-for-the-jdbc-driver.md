---
title: Справочник по API Always Encrypted для JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79cf8ce1b951621d58105d18b847306ff620d114
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028478"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Справочник по API Always Encrypted для JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Функция Always Encrypted позволяет клиентам шифровать конфиденциальные данные в клиентских приложениях, не раскрывая ключи шифрования для SQL Server. Драйвер с поддержкой Always Encrypted, установленный на клиентском компьютере, реализует эту функцию за счет автоматического шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер шифрует данные из конфиденциальных столбцов перед их передачей в SQL Server и автоматически переписывает запросы, чтобы сохранить семантику приложения. Аналогичным образом драйвер прозрачно расшифровывает данные, хранящиеся в столбцах зашифрованной базы данных, которые содержатся в результатах запроса. Дополнительные сведения см. в статьях [Always encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [Использование Always encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted поддерживается только Microsoft JDBC Driver 6.0 или более поздней версии для SQL Server с SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Справочники по API Always Encrypted
 
 Существует несколько дополнений и изменений для API драйвера JDBC для использования в клиентских приложениях, использующих функцию Always Encrypted.  
  
 **Класс SQLServerConnection**  
  
|Имя|Описание|  
|----------|-----------------|  
|Новое ключевое слово строки подключения:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled включает функцию Always Encrypted для подключения, а columnEncryptionSetting=Disabled отключает ее. Допустимыми являются значения Enabled/Disabled. По умолчанию установлено значение Disabled.|  
|Новые методы:<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Позволяет задавать, обновлять и удалять список доверенных путей ключа для сервера базы данных. Если при обработке запроса приложения драйвер получает путь ключа, которого нет в списке, запрос завершается с ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих отправку скомпрометированным SQL Server фиктивных путей ключа, которые могут привести к утечке учетных данных хранилища ключей.|  
|Новый метод:<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Возвращает список доверенных путей ключа для сервера базы данных.|  
|Новый метод:<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Позволяет регистрировать пользовательские поставщики хранилища ключей. Это словарь, сопоставляющий имена поставщиков хранилища ключей с реализациями поставщиков хранилища ключей.<br /><br /> Для использования хранилища ключей виртуальной машины Java необходимо создать экземпляр объекта SQLServerColumnEncryptionJVMKeyStoreProvider с помощью учетных данных хранилища ключей виртуальной машины Java и зарегистрировать его с помощью драйвера. Имя этого поставщика должно быть в виде MSSQL_JVM_KEYSTORE.<br /><br /> Чтобы использовать хранилище Azure Key Vault, необходимо создать экземпляр объекта Склсерверколумненкриптионазурекэйсторепровидер и зарегистрировать его с помощью драйвера. Имя этого поставщика должно быть "AZURE_KEY_VAULT".|
|`public final boolean getSendTimeAsDatetime()`|Возвращает значение свойства соединения Сендтимеасдатетиме.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Изменяет значение свойства соединения Сендтимеасдатетиме.|

 **Класс Склсерверконнектионпулпрокси**
 
|Имя|Описание|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Возвращает значение свойства соединения Сендтимеасдатетиме.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Изменяет значение свойства соединения Сендтимеасдатетиме.|
     
  
 **Класс SQLServerDataSource Class**  
  
|Имя|Описание|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Включает или отключает функцию Always Encrypted для объекта источника данных.<br /><br /> По умолчанию установлено значение Disabled.|  
|`public String getColumnEncryptionSetting()`|Получает параметр функции Always Encrypted для объекта источника данных.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Задает имя, идентифицирующее хранилище ключей. Поддерживается только значение **JavaKeyStorePassword** для идентификации хранилища ключей Java.<br/><br/>Значение по умолчанию — NULL.|
|`public String getKeyStoreAuthentication()`|Возвращает значение параметра keyStoreAuthentication для объекта источника данных.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Задает пароль для хранилища ключей Java. Пароль для хранилища ключей и ключ должен быть одинаковым. Обратите внимание, что keyStoreAuthentication должен быть задан с помощью **JavaKeyStorePassword**.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Задает расположение, включая имя файла для хранилища ключей Java. Обратите внимание, что keyStoreAuthentication должен быть задан с помощью **JavaKeyStorePassword**.|
|`public String getKeyStoreLocation()`|Извлекает keyStoreLocation для хранилища ключей Java.|
  
 **Класс Склсерверколумненкриптионжавакэйсторепровидер**  
  
 Реализация поставщика хранилища ключей для хранилища ключей Java. Этот класс позволяет использовать сертификаты, находящиеся в хранилище ключей Java, в качестве главных ключей столбца.  
  
 Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Поставщик хранилища ключей для хранилища ключей Java.|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Расшифровывает указанное зашифрованное значение ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Путь ключа должен иметь один из следующих форматов.**<br /><br /> Отпечаток:<отпечаток_сертификата><br /><br /> Псевдоним:<псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Шифрует ключ шифрования столбца с помощью сертификата по указанному пути ключа и с помощью указанного алгоритма.<br /><br /> **Путь ключа должен иметь один из следующих форматов.**<br /><br /> Отпечаток:<отпечаток_сертификата><br /><br /> Псевдоним:<псевдоним_сертификата><br /><br /> (Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public void setName (String name)`|Задает имя этого поставщика хранилища ключей.|
|`public String getName ()`|Возвращает имя этого поставщика хранилища ключей.|
  
 **Класс SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Реализация поставщика хранилища ключей для Azure Key Vault. Этот класс позволяет использовать ключи, хранящиеся в Azure Key Vault в качестве главных ключей столбцов.  
  
 Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Поставщик хранилища ключей для Azure Key Vault.  Необходимо указать идентификатор и ключ клиента, запрашивающего маркер для проверки подлинности в Azure Key Vault.|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Расшифровывает ключ шифрования зашифрованного столбца (CEK). Расшифровка выполняется с помощью алгоритма RSA-шифрования, который использует асимметричный ключ, заданный путем к главному ключу.<br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Шифрует ключ шифрования столбца, присваивая указанный главный ключ столбца указанному алгоритму.<br />(Переопределяет SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).) |  
|`public void setName (String name)`|Задает имя этого поставщика хранилища ключей.|
|`public String getName ()`|Возвращает имя этого поставщика хранилища ключей.|  
  
  
 **Интерфейс Склсерверкэйваултаусентикатионкаллбакк**  
  
 Этот интерфейс содержит один метод для Azure Key Vault проверки подлинности, который должен быть реализован пользователем.  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|Необходимо переопределить метод. Метод используется для получения маркера доступа Azure Key Vault.|  
  
 **Класс SQLServerColumnEncryptionKeyStoreProvider**  
  
 Расширьте этот класс для реализации пользовательского поставщика хранилища ключей.  
  
|Имя|Описание|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Базовый класс для всех поставщиков хранилища ключей. Пользовательский поставщик должен наследовать от этого класса и переопределять его функции-члены, а затем регистрировать его с помощью SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Метод базового класса для расшифровки указанного зашифрованного значения ключа шифрования столбца. Зашифрованное значение должно быть зашифровано с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Метод базового класса для шифрования ключа шифрования столбца с помощью главного ключа столбца по указанному пути ключа и с помощью указанного алгоритма.|
|`public abstract void setName(String name)`|Задает имя этого поставщика хранилища ключей.|
|`public abstract String getName()`|Возвращает имя этого поставщика хранилища ключей.|  
  
 Новые или перегруженные методы в классе **SQLServerPreparedStatement**  
  
|Имя|Описание|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Эти методы перегружены с помощью аргумента точности или масштаба или и того, и другого для поддержки Always Encrypted для конкретных типов данных, для которых требуются сведения о точности и масштабе.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Эти методы добавляются для поддержки Always Encrypted для типов данных money, smallmoney, uniqueidentifier, DateTime и smalldatetime. <br/><br/>Обратите внимание, `setTimestamp()` что существующий метод используется для отправки значений параметров в зашифрованный столбец datetime2. Для зашифрованных столбцов datetime и smalldatetime используются новые методы `setDateTime()` и `setSmallDateTime()` соответственно.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Задает указанному параметру заданное значение типа Java.<br /><br /> Если для логического Форцеенкрипт задано значение true, параметр запроса будет установлен только в том случае, если столбец является зашифрованным, а Always Encrypted включен в соединении или в инструкции.<br /><br /> Если для логического Форцеенкрипт задано значение false, драйвер не будет принудительно выполнять шифрование параметров.|  
  
 Новые или перегруженные методы в классе **SQLServerCallableStatement**  
  
|Имя|Описание|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Эти методы перегружены с помощью аргумента точности или масштаба или и того, и другого для поддержки Always Encrypted для конкретных типов данных, для которых требуются сведения о точности и масштабе.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Эти методы добавляются для поддержки Always Encrypted для типов данных money, smallmoney, uniqueidentifier, DateTime и smalldatetime. <br/><br/>Обратите внимание, `setTimestamp()` что существующий метод используется для отправки значений параметров в зашифрованный столбец datetime2. Для зашифрованных столбцов datetime и smalldatetime используются новые методы `setDateTime()` и `setSmallDateTime()` соответственно.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Задает указанному параметру заданное значение типа Java.<br /><br /> Если для логического Форцеенкрипт задано значение true, параметр запроса будет установлен только в том случае, если столбец является зашифрованным, а Always Encrypted включен в соединении или в инструкции.<br /><br /> Если для логического Форцеенкрипт задано значение false, драйвер не будет принудительно выполнять шифрование параметров.|
 

 Новые или перегруженные методы в классе **SQLServerResultSet**  
  
|Имя|Описание|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Эти методы добавляются для поддержки Always Encrypted для типов данных money, smallmoney, uniqueidentifier, DateTime и smalldatetime. <br/><br/>Обратите внимание, `updateTimestamp()` что существующий метод используется для обновления зашифрованных столбцов datetime2. Для зашифрованных столбцов datetime и smalldatetime используются новые методы `updateDateTime()` и `updateSmallDateTime()` соответственно.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Обновление указанного столбца до заданного значения Java.<br/><br/>Если для логического Форцеенкрипт задано значение true, то столбец будет установлен только в том случае, если он зашифрован, а Always Encrypted включен для соединения или инструкции.<br/><br/>Если для логического Форцеенкрипт задано значение false, драйвер не будет принудительно выполнять шифрование параметров.|

  
Новые типы в классе **Microsoft. SQL. types**

|Имя|Описание|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Используйте эти типы в качестве целевых типов SQL при отправке значений параметров в **зашифрованные** столбцы datetime, smalldatetime, Money, smallmoney и `setObject()/updateObject()` uniqueidentifier с помощью методов API.|  
  
  
 **Перечисление Склсерверстатементколумненкриптионсеттинг**  
  
 Указывает, как будут отправляться и приниматься данные при чтении и записи зашифрованных столбцов. В зависимости от конкретного запроса влияние на производительность может снизиться за счет обхода обработки Always Encrypted драйвера при использовании незашифрованных столбцов. Обратите внимание, что эти параметры нельзя использовать для обхода шифрования и получения доступа к данным в виде открытого текста.  
  
 **Синтаксис**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Члены**  
  
|Имя|Описание|  
|----------|-----------------|  
|усеконнектионсеттинг|Указывает, что команда должна по умолчанию Always Encrypted параметру в строке подключения.|  
|Активировано|Включает Always Encrypted для запроса.|  
|ресултсетонли|Указывает, что только результаты команды должны обрабатываться подпрограммой Always Encrypted в драйвере. Используйте это значение, если команда не имеет параметров, требующих шифрования.|  
|Выключено|Отключает Always Encrypted для запроса.|  
  
 Параметр уровня инструкции AE добавляется в класс SQLServerConnection и в класс Склсерверконнектионпулпрокси. Следующие методы в этих классах перегружаются с новым параметром.  
  
|Имя|Описание|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Создает объект инструкции, который будет формировать объекты ResultSet с заданным типом, параллелизмом, удержанием и параметром шифрования столбца.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Создает объект CallableStatement с заданным параметром шифрования столбца, который будет формировать объекты ResultSet с заданным типом, параллелизмом и удержанием.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Создает объект PreparedStatement с заданным параметром шифрования столбца, который имеет возможность получать автоматически созданные ключи.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Создает объект PreparedStatement с заданным параметром шифрования столбца, который будет формировать объекты ResultSet с заданными именами столбцов.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Создает объект PreparedStatement с заданным параметром шифрования столбца, который будет формировать объекты ResultSet с заданными индексами столбца.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Создает объект PreparedStatement с заданным параметром шифрования столбца, который будет формировать объекты ResultSet с заданным типом, параллелизмом и удержанием.|  
  
> [!NOTE]  
>  Если для запроса отключен Always Encrypted, а в запросе есть параметры, которые должны быть зашифрованы (параметры, соответствующие зашифрованным столбцам), запрос завершится ошибкой.  
>   
>  Если Always Encrypted для запроса отключена и запрос возвращает результаты из зашифрованных столбцов, запрос возвратит зашифрованные значения. Зашифрованные значения будут иметь тип данных varbinary.  
  
 ## <a name="see-also"></a>См. также раздел  
 [Использование функции Always Encrypted с JDBC Driver](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

