---
title: Диспетчер подключений Hadoop. Службы SQL Server Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadoopconn.f1
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 051fb627684e8a094ac0f39d5fffad9d9e399d0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841632"
---
# <a name="hadoop-connection-manager"></a>Диспетчер подключений Hadoop
  Диспетчер подключений Hadoop позволяет пакету служб SQL Server Integration Services (SSIS) подключаться к кластеру Hadoop с помощью значений, задаваемых для свойств.  
  
## <a name="configure-the-hadoop-connection-manager"></a>Настройка диспетчера подключений Hadoop  
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** последовательно выберите **Hadoop** > **Добавить**. Будет открыто диалоговое окно **Редактор диспетчера соединений Hadoop** .  
  
2.  Чтобы указать соответствующие сведения о кластере Hadoop, выберите вкладку **WebHCat** или **WebHDFS** в области слева.
  
3.  Если вы включили параметр **WebHCat** для вызова задания Hive или Pig в Hadoop, выполните следующие действия. 
  
    1.  Для параметра **Узел WebHCat** укажите сервер, на котором размещена служба WebHCat.  
  
    2.  Для параметра **WebHCat Port**(Порт WebHCat) укажите порт службы WebHCat (по умолчанию — 50111).  
  
    3.  Выберите метод **аутентификации** доступа к службе WebHCat. Доступные значения: **Обычная** и **Kerberos**.  
  
         ![Снимок экрана редактора диспетчера подключений Hadoop с обычной проверкой подлинности](../../integration-services/connection-manager/media/hadoop-cm-basic.png "Hadoop connection manager editor with basic authentication")  
  
         ![Снимок экрана редактора диспетчера подключений Hadoop с проверкой подлинности Kerberos](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Hadoop connection manager editor with Kerberos authentication")  
  
    4.  Для параметра **WebHCat User**(Пользователь WebHCat) укажите **пользователя** с правом доступа к WebHCat.  
  
    5.  Если вы выбрали аутентификацию **Kerberos** , введите **пароль** и **домен**пользователя.  
  
4.  Если включен параметр **WebHDFS** для копирования данных из файловой системы HDFS или в нее, выполните следующие действия: 
  
    1.  Для параметра **WebHDFS Host**(Узел WebHDFS) укажите сервер, на котором размещена служба WebHDFS.  
  
    2.  Для параметра **WebHDFS Port**(Порт WebHDFS) укажите порт службы WebHDFS (по умолчанию — 50070).  
  
    3.  Выберите метод **аутентификации** доступа к службе WebHDFS. Доступные значения: **Обычная** и **Kerberos**.  
  
    4.  Для параметра **WebHDFS User**(Пользователь WebHDFS) укажите пользователя с правом доступа к HDFS.  
  
    5.  Если вы выбрали аутентификацию **Kerberos** , введите **пароль** и **домен**пользователя.  
  
5.  Нажмите кнопку **Проверить подключение**. (Проверяется только включенное вами подключение.)  
  
6.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК**.  

## <a name="connect-with-kerberos-authentication"></a>Подключение с использованием проверки подлинности Kerberos
Чтобы использовать проверку подлинности Kerberos с диспетчером соединений Hadoop, локальную среду можно настроить двумя способами. Вы можете выбрать лучший вариант.
-   Вариант 1. [Присоединение компьютера со службами SSIS к области Kerberos](#kerberos-join-realm)
-   Вариант 2. [Включение взаимного доверия между доменом Windows и областью Kerberos](#kerberos-mutual-trust)

### <a name="kerberos-join-realm"></a>Вариант 1. Присоединение компьютера со службами SSIS к области Kerberos

#### <a name="requirements"></a>Требования

-   Компьютер шлюза нужно подключить к области Kerberos. При этом он не должен подключаться к доменам Windows.

#### <a name="how-to-configure"></a>Порядок настройки:

На компьютере со службами SSIS сделайте следующее:

1.  Запустите служебную программу **Ksetup**, чтобы настроить сервер центра распространения ключей (KDC) и область Kerberos.

    Компьютер нужно настроить в качестве члена рабочей группы, так как область Kerberos отличается от домена Windows. Задайте область Kerberos и добавьте сервер KDC, как показано в примере ниже. При необходимости замените `REALM.COM` значением своей соответствующей области.

    ```    
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
    ```

    Выполнив эти команды, перезагрузите компьютер.

2.  Проверьте конфигурацию с помощью команды **Ksetup**. Выходные данные должны выглядеть так, как в следующем примере:

    ```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
    ```

### <a name="kerberos-mutual-trust"></a>Вариант 2. Включение взаимного доверия между доменом Windows и областью Kerberos

#### <a name="requirements"></a>Требования
-   Необходимо подключить компьютер шлюза к домену Windows.
-   Требуется разрешение на обновление параметров контроллера домена.

#### <a name="how-to-configure"></a>Порядок настройки:

> [!NOTE]
> При необходимости замените `REALM.COM` и `AD.COM` значениями своей соответствующей области и контроллера домена в следующих инструкциях.

На сервере KDC сделайте следующее:

1.  Измените конфигурацию KDC в файле **krb5.conf**. Разрешите KDC доверять домену Windows, ссылаясь на следующий шаблон конфигурации. По умолчанию файл конфигурации содержится в папке **/etc/krb5.conf**.

    ```
    [logging]
    default = FILE:/var/log/krb5libs.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmind.log

    [libdefaults]
    default_realm = REALM.COM
    dns_lookup_realm = false
    dns_lookup_kdc = false
    ticket_lifetime = 24h
    renew_lifetime = 7d
    forwardable = true

    [realms]
    REALM.COM = {
        kdc = node.REALM.COM
        admin_server = node.REALM.COM
        }
    AD.COM = {
        kdc = windc.ad.com
        admin_server = windc.ad.com
        }

    [domain_realm]
    .REALM.COM = REALM.COM
    REALM.COM = REALM.COM
    .ad.com = AD.COM
    ad.com = AD.COM

    [capaths]
    AD.COM = {
        REALM.COM = .
        }
    ```

    Перезагрузите службу KDC после настройки.

2.  Подготовьте субъект с именем **krbtgt/REALM.COM@AD.COM** на сервере KDC. Используйте следующую команду:

    `Kadmin> addprinc krbtgt/REALM.COM@AD.COM`

3.  В файл конфигурации службы HDFS **hadoop.security.auth_to_local** добавьте `RULE:[1:$1@$0](.*@AD.COM)s/@.*//`.

На контроллере домена сделайте следующее:

1.  Выполните следующие команды **Ksetup**, чтобы добавить запись области.

    ```
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
    C:> ksetup /addhosttorealmmap HDFS-service-FQDN REALM.COM
    ```

2.  Установите доверие между доменом Windows и областью Kerberos. В следующем примере `[password]` представляет собой пароль для субъекта **krbtgt/REALM.COM@AD.COM**.

    `C:> netdom trust REALM.COM /Domain: AD.COM /add /realm /password:[password]`

3.  Выберите алгоритм шифрования для использования с Kerberos.

    1. Последовательно выберите **Диспетчер сервера** > **Управление групповой политикой** > **Домен**. После этого выберите **Объекты групповой политики** > **политику домена по умолчанию или активную политику домена** > **Изменить**.

    2. Во всплывающем окне **Редактор управления групповыми политиками последовательно** выберите **Конфигурация компьютера** > **Политики** > **Параметры Windows**. После этого выберите **Настройки безопасности** > **Локальные политики** > **Параметры безопасности**. Настройте политику **Сетевая безопасность: настройка типов шифрования, разрешенных Kerberos**.

    3. Выберите алгоритм шифрования, который будет использоваться для подключения к KDC. Как правило, можно выбрать любой параметр.

        ![Снимок экрана типов шифрования для Kerberos](media/hadoop-connection-manager/config-encryption-types-for-kerberos.png)

    4. Чтобы указать алгоритм шифрования для использования в определенной области, используйте команду **Ksetup**.

        `C:> ksetup /SetEncTypeAttr REALM.COM DES-CBC-CRC DES-CBC-MD5 RC4-HMAC-MD5 AES128-CTS-HMAC-SHA1-96 AES256-CTS-HMAC-SHA1-96`

4.  Чтобы использовать субъект Kerberos в домене Windows, создайте сопоставление между учетной записью домена и субъектом Kerberos.

    1. Последовательно выберите **Администрирование** > **Active Directory — пользователи и компьютеры**.

    2. Настройте дополнительные функции, выбрав **Вид** > **Дополнительные параметры**.

    3. Найдите учетную запись, для которой нужно создать сопоставления, щелкните ее правой кнопкой мыши, чтобы выбрать пункт **Отображение имен**, а затем выберите вкладку **Имена Kerberos**.

    4. Добавьте субъект из области.

        ![Снимок экрана диалогового окна "Сопоставление объекта безопасности"](media/hadoop-connection-manager/map-security-identity.png)

На компьютере со шлюзом сделайте следующее:

Выполните следующие команды **Ksetup**, чтобы добавить запись области.

    ```
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
    C:> ksetup /addhosttorealmmap HDFS-service-FQDN REALM.COM
    ```

## <a name="see-also"></a>См. также раздел  
 [Задача Hadoop Hive](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Задача Pig для Hadoop](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Задача файловой системы Hadoop](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  
