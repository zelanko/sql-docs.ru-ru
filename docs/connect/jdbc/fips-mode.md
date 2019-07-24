---
title: Режим FIPS в JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
manager: kenvh
ms.openlocfilehash: 482e820d17860b67f46d47f4bb8523e833d0cf5a
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68252215"
---
# <a name="fips-mode"></a>Режим FIPS

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер Microsoft JDBC для SQL Server поддерживает работу в виртуальных машин Java, для которой настроено *соответствие стандарту FIPS 140*.

#### <a name="prerequisites"></a>предварительные требования

- Настроенный FIPS ВИРТУАЛЬНОЙ машины Java
- Соответствующий SSL-сертификат
- Соответствующие файлы политики
- Соответствующие параметры конфигурации

## <a name="fips-configured-jvm"></a>Настроенный FIPS ВИРТУАЛЬНОЙ машины Java

Как правило, приложения могут настроить `java.security` для файла использование FIPS совместимых поставщиков шифрования. Сведения о настройке соответствия FIPS 140 см. в документации, относящейся к вашей ВИРТУАЛЬНОЙ машины Java.

Чтобы просмотреть утвержденные модули для конфигурации FIPS, см. раздел [проверенные модули в программе проверки криптографических](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules)модулей.

Поставщики могут выполнять некоторые дополнительные действия по настройке ВИРТУАЛЬНОЙ машины Java с FIPS.

## <a name="appropriate-ssl-certificate"></a>Соответствующий SSL-сертификат
Чтобы подключиться к SQL Server в режиме FIPS, требуется действительный SSL-сертификат. Установите или импортируйте его в хранилище ключей Java на клиентском компьютере (ВИРТУАЛЬНОЙ машины Java), где включен FIPS.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Импорт SSL-сертификата в хранилище ключей Java
Для FIPS, скорее всего, потребуется импортировать сертификат (CERT) в формат PKCS или в формате, характерном для поставщика.
Используйте следующий фрагмент кода, чтобы импортировать SSL-сертификат и сохранить его в рабочем каталоге с соответствующим форматом хранилища ключей. _Пароль\_доверенного хранилища\__ — это пароль для хранилища ключей Java.

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

В следующем примере импортируется SSL-сертификат Azure в формате PKCS12 с поставщиком Баунцикастле. Сертификат импортируется в рабочий каталог с именем _митрустсторе\_PKCS12_ с помощью следующего фрагмента кода:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Соответствующие файлы политики
Для некоторых поставщиков FIPS требуется неограниченная политика JAR. В таких случаях для Sun/Oracle Скачайте файлы политики юрисдикции расширения криптографии Java (ЖЦЕ) для [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) или [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Соответствующие параметры конфигурации
Чтобы запустить драйвер JDBC в режиме, совместимом с FIPS, настройте свойства соединения, как показано в следующей таблице. 

#### <a name="properties"></a>Свойства 

|Свойство|Тип|По умолчанию|Описание|Примечания|
|---|---|---|---|---|
|encrypt|Boolean ["true/false"]|"false"|Для свойства шифрования ВИРТУАЛЬНОЙ машины Java с поддержкой FIPS должно быть задано **значение true**||
|TrustServerCertificate|Boolean ["true/false"]|"false"|Для FIPS пользователь должен проверить цепочку сертификатов, чтобы пользователь использовал значение **"false"** для этого свойства. ||
|trustStore|String|null|Путь к файлу хранилища ключей Java, в котором был импортирован сертификат. Если установить сертификат в системе, не нужно ничего передавать. Драйвер использует файлы cacerts или жссекацертс.||
|trustStorePassword|String|null|Пароль, используемый для проверки целостности данных trustStore.||
|fips|Boolean ["true/false"]|"false"|Для FIPS Enabled ВИРТУАЛЬНОЙ машины Java это свойство должно иметь **значение true** .|Добавлено в 6.1.4 (стабильный выпуск 6.2.2)||
|fipsProvider|String|null|Поставщик FIPS, настроенный в ВИРТУАЛЬНОЙ машины Java. Например, БКФИПС или SunPKCS11-NSS |Добавлен в 6.1.2 (стабильный выпуск 6.2.2), устаревший в 6.4.0. подробности см. [здесь](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|трустсторетипе|String|JKS-|Для режима FIPS задайте для параметра Trust Store Type тип PKCS12 или тип, определенный поставщиком FIPS. |Добавлено в 6.1.2 (стабильный выпуск 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
