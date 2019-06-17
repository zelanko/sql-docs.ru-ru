---
title: Режим FIPS в JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: craigg
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: kenvh
ms.openlocfilehash: d710bb6e83d6f9761f7926afac3280a2c33d2bec
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822233"
---
# <a name="fips-mode"></a>Режим FIPS

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver для SQL Server поддерживает работу в JVM, настроенного *с FIPS 140*.

#### <a name="prerequisites"></a>предварительные требования

- FIPS настроенной виртуальной машине Java
- Соответствующий SSL-сертификата
- Соответствующие политики файлов
- Соответствующие параметры.

## <a name="fips-configured-jvm"></a>FIPS настроенной виртуальной машине Java

Как правило, можно настроить приложения `java.security` файл для использования FIPS требованиям шифрования поставщиков. См. в документации по виртуальной машины Java, сведения о настройке соответствия FIPS 140.

Утвержденные модули FIPS конфигурации, можно найти по [проверки модулей в программе проверки криптографического модуля](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules).

Поставщики могут иметь некоторые дополнительные действия по настройке виртуальной машины Java с FIPS.

## <a name="appropriate-ssl-certificate"></a>Соответствующий SSL-сертификата
Чтобы подключиться к SQL Server в режиме FIPS, необходим действительный сертификат SSL. Установите или импортировать его в Java Key Store на клиентском компьютере (JVM) где система FIPS включена.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Импорт SSL-сертификат в хранилище ключей Java
Для FIPS скорее всего необходимо импортировать сертификат (.cert) в формате конкретного поставщика или PKCS.
Используйте следующий фрагмент кода для импорта SSL-сертификат и сохранить его в рабочий каталог на соответствующий формат хранилища ключей. _ДОВЕРЯТЬ\_ХРАНИЛИЩЕ\_пароль_ — это пароль для хранилища ключей Java.

```java
public void saveGenericKeyStore(
        String provider,
        String trustStoreType,
        String certName,
        String certPath
        ) throws KeyStoreException, CertificateException,
            NoSuchAlgorithmException, NoSuchProviderException,
            IOException
{
    KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
    FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
    ks.load(null, null);
    ks.setCertificateEntry(certName, getCertificate(certPath));
    ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
    os.flush();
    os.close();
}

private Certificate getCertificate(String pathName)
        throws FileNotFoundException, CertificateException
{
    FileInputStream fis = new FileInputStream(pathName);
    CertificateFactory cf = CertificateFactory.getInstance("X.509");
    return cf.generateCertificate(fis);
}
```

В следующем примере выполняется импорт SSL-сертификат Azure в формате PKCS12 с поставщиком BouncyCastle. Сертификат будет импортирован в рабочем каталоге с именем _MyTrustStore\_PKCS12_ , используя следующий фрагмент кода:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Соответствующие политики файлов
Некоторые поставщики предоставляют FIPS необходимы неограниченный JAR-файлы политики. В таком случае для Sun / Oracle, скачать Java Cryptography Extension (JCE) неограниченное стойкость файлы политики юрисдикции для [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) или [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Соответствующие параметры.
Чтобы запустить драйвер JDBC в режиме совместимости с FIPS, настройте свойства соединения, как показано в следующей таблице. 

#### <a name="properties"></a>Свойства 

|Свойство|Тип|По умолчанию|Описание|Примечания|
|---|---|---|---|---|
|encrypt|Логическое значение [«true / false»]|"false"|Для включенных FIPS JVM шифровать свойство должно быть **true**||
|TrustServerCertificate|Логическое значение [«true / false»]|"false"|Для FIPS, необходимые пользователю для проверки цепочки сертификатов, поэтому пользователь должен использовать **«false»** значение этого свойства. ||
|trustStore|String|null|Хранилище ключей Java путь к файлу где импортировать сертификат. При установке сертификата на компьютере, то не нужно передать все что угодно. Драйвер использует cacerts или jssecacerts файлов.||
|trustStorePassword|String|null|Пароль, используемый для проверки целостности данных trustStore.||
|fips|Логическое значение [«true / false»]|"false"|Для виртуальной машины Java с поддержкой FIPS это свойство должно иметь **true**|Добавлен в 6.1.4 (стабильный выпуск 6.2.2)||
|fipsProvider|String|null|Поставщик FIPS, настроенные в виртуальной машине Java. Например, BCFIPS или SunPKCS11 NSS |Добавлен в 6.1.2 (стабильной выпуска 6.2.2), рекомендуется использовать в 6.4.0 - см. в разделе сведений [здесь](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Для типа хранилища доверия для набора FIPS режима PKCS12 или тип определены поставщиком FIPS |Добавлен в 6.1.2 (стабильный выпуск 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
