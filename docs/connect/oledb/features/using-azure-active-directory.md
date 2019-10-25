---
title: Использование Azure Active Directory | Документация Майкрософт для SQL Server
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: b459877be731da11b33d13772bbf186ecf72198c
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381853"
---
# <a name="using-azure-active-directory"></a>Использование Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Назначение

Начиная с версии 18.2.1 драйвер Microsoft OLE DB для SQL Server позволяет приложениям OLE DB подключаться к экземпляру базы данных SQL Azure с помощью федеративного удостоверения. Новые методы проверки подлинности включают:
- Идентификатор входа Azure Active Directory и пароль
- Маркер доступа Azure Active Directory
- Интегрированная проверка подлинности Azure Active Directory
- ИДЕНТИФИКАТОР и пароль для входа SQL

В версии 18,3 добавлена поддержка следующих методов проверки подлинности:
- Интерактивная проверка подлинности Azure Active Directory
- Проверка подлинности MSI Azure Active Directory

> [!NOTE]
> Использование следующих режимов проверки подлинности с `DataTypeCompatibility` (или его соответствующим свойством), имеющим значение `80`, **не** поддерживается:
> - Проверка подлинности Azure Active Directory с помощью идентификатора входа и пароля
> - Проверка подлинности Azure Active Directory с помощью маркера доступа
> - Интегрированная проверка подлинности Azure Active Directory
> - Интерактивная проверка подлинности Azure Active Directory
> - Проверка подлинности MSI Azure Active Directory

## <a name="connection-string-keywords-and-properties"></a>Ключевые слова и свойства строки подключения
Для поддержки проверки подлинности Azure Active Directory были введены следующие ключевые слова строки подключения:

|Ключевое слово строки подключения|Свойства подключения|Описание|
|---               |---                |---        |
|Маркер доступа|SSPROP_AUTH_ACCESS_TOKEN|Указывает маркер доступа для проверки подлинности в Azure Active Directory. |
|Проверка подлинности|SSPROP_AUTH_MODE|Указывает используемый метод проверки подлинности.|

Дополнительные сведения о новых ключевых словах и свойствах см. на следующих страницах:
- [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Свойства инициализации и авторизации](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Шифрование и проверка сертификатов
В этом разделе обсуждаются изменения в правилах шифрования и проверки сертификатов. Эти изменения вступают в силу **только** при использовании новых ключевых слов проверки подлинности или строки подключения маркера доступа (или их соответствующих свойств).

### <a name="encryption"></a>Шифрование
Для повышения безопасности при использовании новых свойств или ключевых слов соединения драйвер переопределяет значение шифрования по умолчанию, присвоив его `yes`. Переопределение происходит во время инициализации объекта источника данных. Если шифрование задается до инициализации любым способом, значение учитывается и не переопределяется.

> [!NOTE]   
> В приложениях ADO и приложениях, которые получают интерфейс `IDBInitialize` через `IDataInitialize::GetDataSource`, основной компонент, реализующий интерфейс, явно устанавливает шифрование в значение по умолчанию `no`. В результате новые свойства или ключевые слова проверки подлинности, относящиеся к этому параметру, и значение шифрования **не** переопределяются. Поэтому **рекомендуется** явно задать для этих приложений `Use Encryption for Data=true` переопределить значение по умолчанию.

### <a name="certificate-validation"></a>Проверка сертификатов
Для повышения безопасности новые свойства или ключевые слова соединения учитывают параметр `TrustServerCertificate` (и соответствующие ключевые слова и свойства строки подключения) **независимо от параметра шифрования клиента**. В результате сертификат сервера проверяется по умолчанию.

> [!NOTE]   
> Проверку сертификата можно также контролировать с помощью поля `Value` записи реестра `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2`. Допустимые значения: `0` или `1`. Драйвер OLE DB выбирает наиболее безопасный вариант между реестром и параметрами свойства соединения/ключевого слова. То есть драйвер будет проверять сертификат сервера, если по крайней мере один из параметров реестра или подключения включает проверку сертификата сервера.

## <a name="gui-additions"></a>Добавление графических интерфейсов
Графический пользовательский интерфейс драйвера был усовершенствован, чтобы обеспечить Azure Active Directoryную проверку подлинности. Дополнительные сведения см. в разделе:
- [Диалоговое окно входа SQL Server](../help-topics/sql-server-login-dialog.md)
- [Конфигурация универсального канала передачи данных (UDL)](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Примеры строк подключения
В этом разделе приведены примеры новых и существующих ключевых слов строки подключения для использования со свойствами `IDataInitialize::GetDataSource` и `DBPROP_INIT_PROVIDERSTRING`.

### <a name="sql-authentication"></a>Проверка подлинности SQL
- Использование среды `IDataInitialize::GetDataSource`:
    - Добавления:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = SqlPassword**; Идентификатор пользователя = [username]; Password = [пароль]; Использовать шифрование для data = true
    - Устарело:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; Идентификатор пользователя = [username]; Password = [пароль]; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    - Добавления:
        > Server = [сервер];D Аза данных = [база данных]; **Authentication = SqlPassword**; UID = [username]; PWD = [пароль]; Шифровать = да
    - Устарело:
        > Server = [сервер];D Аза данных = [база данных]; UID = [username]; PWD = [пароль]; Шифровать = да

### <a name="integrated-windows-authentication-using-security-support-provider-interface-sspi"></a>Встроенная проверка подлинности Windows с помощью интерфейса поставщика поддержки безопасности (SSPI)

- Использование среды `IDataInitialize::GetDataSource`:
    - Добавления:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Использовать шифрование для data = true
    - Устарело:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Integrated Security = SSPI**; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    - Добавления:
        > Server = [сервер];D Аза данных = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Шифровать = да
    - Устарело:
        > Server = [сервер];D Аза данных = [база данных]; **Trusted_Connection = да**; Шифровать = да

### <a name="azure-active-directory-username-and-password-authentication"></a>Azure Active Directory проверка подлинности имени пользователя и пароля

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = ActiveDirectoryPassword**; Идентификатор пользователя = [username]; Password = [пароль]; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [сервер];D Аза данных = [база данных]; **Authentication = ActiveDirectoryPassword**; UID = [username]; PWD = [пароль]; Шифровать = да

### <a name="azure-active-directory-integrated-authentication"></a>Интегрированная проверка подлинности Azure Active Directory

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [сервер];D Аза данных = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Шифровать = да

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Проверка подлинности Azure Active Directory с помощью маркера доступа

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Маркер доступа = [маркер доступа]** ; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Предоставление маркера доступа через `DBPROP_INIT_PROVIDERSTRING` не поддерживается

### <a name="azure-active-directory-interactive-authentication"></a>Интерактивная проверка подлинности Azure Active Directory

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = активедиректоринтерактиве**; Идентификатор пользователя = [username]; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [сервер];D Аза данных = [база данных]; **Authentication = активедиректоринтерактиве**; UID = [username]; Шифровать = да

### <a name="azure-active-directory-msi-authentication"></a>Проверка подлинности MSI Azure Active Directory

- Использование среды `IDataInitialize::GetDataSource`:
    - Управляемое удостоверение, назначаемое пользователем:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = активедиректоримси**; User ID = [идентификатор объекта]; Использовать шифрование для data = true
    - Управляемое удостоверение, назначаемое системой:
        > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = активедиректоримси**; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    - Управляемое удостоверение, назначаемое пользователем:
        > Server = [сервер];D Аза данных = [база данных]; **Authentication = активедиректоримси**; UID = [идентификатор объекта]; Шифровать = да
    - Управляемое удостоверение, назначаемое системой:
        > Server = [сервер];D Аза данных = [база данных]; **Authentication = активедиректоримси**; Шифровать = да

## <a name="code-samples"></a>Примеры кода

В следующих примерах показан код, необходимый для подключения к Azure Active Directory с ключевыми словами подключения. 

### <a name="access-token"></a>Маркер доступа
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    wchar_t accessToken[] = L"eyJ0eXAiOi...";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Access Token=" + accessToken + L";Use Encryption for Data=true;";
    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```
### <a name="active-directory-integrated"></a>Встроенная проверка подлинности Active Directory
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Authentication=ActiveDirectoryIntegrated;Use Encryption for Data=true;";

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr)) 
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```

## <a name="next-steps"></a>Следующие шаги
- [Авторизуйте доступ к Azure Active Directory веб-приложениям, используя поток предоставления кода OAuth 2,0](https://go.microsoft.com/fwlink/?linkid=2072672).

- Ознакомьтесь со сведениями о [проверке подлинности Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2073783) для SQL Server.

- Настройка подключений к драйверу с помощью [ключевых слов строки подключения](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) , поддерживаемых драйвером OLE DB.
