---
title: "Режим FIPS | Документы Microsoft"
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 1
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f344ad84588110372ccb369ae97642ef6c42f07
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="fips-mode"></a>Режим FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер Microsoft JDBC для SQL Server поддерживает *режиме совместимости с FIPS 140*. Для Oracle / виртуальной машины Java Sun, ссылаться на [совместимого с FIPS 140 режима для SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) раздела, предоставляемого корпорацией Oracle Настройка FIPS включена виртуальной машины Java. 

**Предварительные требования**:
* FIPS настроенной виртуальной машине Java
* Соответствующий SSL-сертификат.
* Файлы соответствующую политику. 
* Параметры в соответствующей конфигурации. 


## <a name="fips-configured-jvm"></a>FIPS настроенной виртуальной машине Java:

Утвержденные модули для конфигурации FIPS, можно найти по [проверка FIPS 140-1 и криптографических модулей FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

Поставщики могут иметь некоторые дополнительные действия по настройке виртуальной машины Java с FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Убедитесь, что в вашей виртуальной машины Java находится в режиме FIPS.
Чтобы убедиться, что в вашей виртуальной машины Java — FIPS включена, выполните следующий фрагмент кода: 

````
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
````

## <a name="appropriate-ssl-certificate"></a>Соответствующий SSL-сертификат:
Для подключения SQL Server в режиме FIPS, требуется действительный сертификат SSL. Установите или импортировать его в Java хранилище ключей на клиентском компьютере (JVM) активированной FIPS. Если не Импорт и установите соответствующий сертификат, вам не удалось подключиться к SQL Server, которые невозможно установить безопасное подключение.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Импорт SSL-сертификата в хранилище ключей Java:
Для FIPS скорее всего необходимо импортировать сертификат (.cert) либо PKCS или в формате конкретного поставщика. Используйте следующий фрагмент, чтобы импортировать сертификат SSL и сохраните его в рабочий каталог на соответствующий формат хранилища ключей. _TRUST_STORE_PASSWORD_ — пароль для хранилища ключей Java. 

````
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

````


В следующем примере мы импортируем SSL-сертификат Azure в формате PKCS12 BouncyCastle поставщика. Импортировать сертификат в рабочем каталоге с именем _MyTrustStore_PKCS12_ , используя следующий фрагмент кода:

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>Файлы подходящей политики: 
Для некоторых поставщиков FIPS необходимы неограниченный JAR-файлов политики. В таких случаях для Sun / Oracle, загрузите Java Cryptography Extension (JCE) неограниченное стойкость файлы политики юрисдикции для [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) или [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Параметры соответствующих настроек: 
Для запуска драйвера JDBC в режиме FIPS-совместимые, настройте свойства подключения, как показано в следующей таблице. 

**Свойства**: 

|Свойство|Тип|По умолчанию|Description|Примечания|
|---|---|---|---|---|
|encrypt|Логическое значение [«true / false»]|«false»|Шифрование FIPS включен виртуальной машины Java свойство должно быть **true**||
|TrustServerCertificate|Логическое значение [«true / false»]|«false»|Для FIPS, нам нужно проверить цепочку сертификатов, поэтому следует использовать **«false»** значение этого свойства. ||
|trustStore|Строковые значения|null|Хранилище ключей Java путь к файлу где импортировать сертификат. Если установить сертификат на компьютер, а затем передать ничего не нужно. Драйвер использует cacerts или jssecacerts файлов.||
|trustStorePassword|Строковые значения|null|Пароль, используемый для проверки целостности данных trustStore.||
|FIPS|Логическое значение [«true / false»]|«false»|Для виртуальной машины Java с поддержкой стандарта fips это свойство должно быть **true**|Добавлено в 6.1.4||
|fipsProvider|Строковые значения|null|Поставщик FIPS, настроенные в виртуальной машины Java. Например, BCFIPS или SunPKCS11 NSS |Добавлено в 6.1.2|
|trustStoreType|Строковые значения|JKS|Для типа хранилища доверия набора режим FIPS PKCS12 или тип определены поставщиком FIPS |Добавлено в 6.1.2||



  

