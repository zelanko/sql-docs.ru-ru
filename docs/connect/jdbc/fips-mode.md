---
title: Режим FIPS | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.openlocfilehash: cc13455e6f56950d6988909b53aa7664c7fd77f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723832"
---
# <a name="fips-mode"></a>Режим FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver для SQL Server поддерживает *совместимого с FIPS 140 режима*. Для Oracle / виртуальной машины Java Sun, ссылаться на [совместимого с FIPS 140 режима для SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) раздел, предоставляемого корпорацией Oracle по настройке FIPS включен виртуальной машины Java. 

**Предварительные требования**:
* FIPS настроенной виртуальной машине Java
* Соответствующий SSL-сертификат.
* Файлы соответствующую политику. 
* Параметры соответствующей конфигурации. 


## <a name="fips-configured-jvm"></a>FIPS настроенной виртуальной машине Java

Утвержденные модули FIPS конфигурации, можно найти по [проверки FIPS 140-1 и криптографические модули FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

Поставщики могут иметь некоторые дополнительные действия по настройке виртуальной машины Java с FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Убедитесь, что виртуальной машины Java в режиме FIPS
Чтобы обеспечить виртуальной машины Java поддержкой FIPS, выполните следующий фрагмент кода: 

```java
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
```

## <a name="appropriate-ssl-certificate"></a>Соответствующий SSL-сертификата
Для подключения к SQL Server в режиме FIPS, необходим действительный сертификат SSL. Установите или импортировать его в Java Key Store на клиентском компьютере (JVM) где система FIPS включена.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Импорт SSL-сертификат в хранилище ключей Java
Для FIPS скорее всего необходимо импортировать сертификат (.cert) либо PKCS или в формате конкретного поставщика. Используйте следующий фрагмент кода для импорта SSL-сертификат и сохранить его в рабочий каталог на соответствующий формат хранилища ключей. _TRUST_STORE_PASSWORD_ — это пароль для хранилища ключей Java. 

```java
    public void saveGenericKeyStore(String provider, String trustStoreType, String certName, String certPath) throws KeyStoreException, CertificateException, NoSuchAlgorithmException, NoSuchProviderException, IOException {
        KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
        FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
        ks.load(null, null);
        ks.setCertificateEntry(certName, getCertificate(certPath));
        ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
        os.flush();
        os.close();
    }

    private Certificate getCertificate(String pathName) throws FileNotFoundException, CertificateException {
        FileInputStream fis = new FileInputStream(pathName);
        CertificateFactory cf = CertificateFactory.getInstance("X.509");
        return cf.generateCertificate(fis);
    }

```


В следующем примере выполняется импорт SSL-сертификат Azure в формате PKCS12 с поставщиком BouncyCastle. Сертификат будет импортирован в рабочем каталоге с именем _MyTrustStore_PKCS12_ , используя следующий фрагмент кода:

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>Соответствующие политики файлов
Некоторые поставщики предоставляют FIPS необходимы неограниченный JAR-файлы политики. В таком случае для Sun / Oracle, скачать Java Cryptography Extension (JCE) неограниченное стойкость файлы политики юрисдикции для [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) или [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Соответствующие параметры.
Чтобы запустить драйвер JDBC в режиме совместимости с FIPS, настройте свойства соединения, как показано в следующей таблице. 

**Свойства**: 

|Свойство|Тип|По умолчанию|Описание|Примечания|
|---|---|---|---|---|
|encrypt|Логическое значение [«true / false»]|"false"|Для включенных FIPS JVM шифровать свойство должно быть **true**||
|TrustServerCertificate|Логическое значение [«true / false»]|"false"|Для FIPS, необходимые пользователю для проверки цепочки сертификатов, поэтому пользователь должен использовать **«false»** значение этого свойства. ||
|trustStore|String|null|Хранилище ключей Java путь к файлу где импортировать сертификат. При установке сертификата на компьютере, то не нужно передать все что угодно. Драйвер использует cacerts или jssecacerts файлов.||
|trustStorePassword|String|null|Пароль, используемый для проверки целостности данных trustStore.||
|fips|Логическое значение [«true / false»]|"false"|Для виртуальной машины Java с поддержкой FIPS это свойство должно иметь **true**|Добавлен в 6.1.4 (стабильный выпуск 6.2.2)||
|fipsProvider|String|null|Поставщик FIPS, настроенные в виртуальной машине Java. Например, BCFIPS или SunPKCS11 NSS |Добавлен в 6.1.2 (стабильной выпуска 6.2.2), рекомендуется использовать в 6.4.0 - см. в разделе сведений [здесь](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Для типа хранилища доверия для набора FIPS режима PKCS12 или тип определены поставщиком FIPS |Добавлен в 6.1.2 (стабильный выпуск 6.2.2)||



  
