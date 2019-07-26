---
title: Использование Azure Active Directory | Документация Майкрософт для SQL Server
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 44f92e782a497005ea47847301279e4341722d36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68213554"
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

> [!NOTE]  
> При использовании следующих параметров Azure Active Directory с драйвером OLE DB убедитесь, что [Библиотека проверки подлинности Active Directory для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) установлена:
> - Идентификатор входа Azure Active Directory и пароль
> - Интегрированная проверка подлинности Azure Active Directory
>
> ADAL не требуется для других методов проверки подлинности или операций OLE DB.

> [!NOTE]
> Использование следующих режимов проверки подлинности с `DataTypeCompatibility` параметром (или его соответствующим свойством), установленным в `80` , **не** поддерживается:
> - Проверка подлинности Azure Active Directory с помощью идентификатора входа и пароля
> - Проверка подлинности Azure Active Directory с помощью маркера доступа
> - Интегрированная проверка подлинности Azure Active Directory

## <a name="connection-string-keywords-and-properties"></a>Ключевые слова и свойства строки подключения
Для поддержки проверки подлинности Azure Active Directory были введены следующие ключевые слова строки подключения:

|Ключевое слово строки подключения|Свойства подключения|Описание|
|---               |---                |---        |
|Маркер доступа|SSPROP_AUTH_ACCESS_TOKEN|Указывает маркер доступа для проверки подлинности в Azure Active Directory. |
|Проверка подлинности|SSPROP_AUTH_MODE|Указывает используемый метод проверки подлинности.|

Дополнительные сведения о новых ключевых словах и свойствах см. на следующих страницах:
- [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Свойства инициализации и авторизации](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Шифрование и проверка сертификата
В этом разделе обсуждаются изменения в правилах шифрования и проверки сертификатов. Эти изменения вступают в силу **только** при использовании новых ключевых слов проверки подлинности или строки подключения маркера доступа (или их соответствующих свойств).

### <a name="encryption"></a>Шифрование
Для повышения безопасности, когда используются новые свойства или ключевые слова соединения, драйвер переопределяет значение шифрования по умолчанию, задавая его `yes`свойству. Переопределение происходит во время инициализации объекта источника данных. Если шифрование задается до инициализации любым способом, значение учитывается и не переопределяется.

> [!NOTE]   
> В приложениях ADO и приложениях, которые получают `IDBInitialize` интерфейс через `IDataInitialize::GetDataSource`, основной компонент, реализующий интерфейс, явно устанавливает шифрование `no`в значение по умолчанию. В результате новые свойства или ключевые слова проверки подлинности, относящиеся к этому параметру, и значение шифрования **не** переопределяются. Поэтому **рекомендуется** явно задать `Use Encryption for Data=true` для этих приложений переопределение значения по умолчанию.

### <a name="certificate-validation"></a>Проверка сертификатов
Для повышения безопасности новые свойства или ключевые слова соединения учитывают `TrustServerCertificate` параметр (и соответствующие ключевые слова и свойства строки подключения) **независимо от параметра шифрования клиента**. В результате сертификат сервера проверяется по умолчанию.

> [!NOTE]   
> Проверку сертификата можно также контролировать с помощью `Value` поля `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` записи реестра. Допустимые значения: `0` или `1`. Драйвер OLE DB выбирает наиболее безопасный вариант между реестром и параметрами свойства соединения/ключевого слова. То есть драйвер будет проверять сертификат сервера, если по крайней мере один из параметров реестра или подключения включает проверку сертификата сервера.

## <a name="gui-additions"></a>Добавление графических интерфейсов
Графический пользовательский интерфейс драйвера был усовершенствован, чтобы обеспечить Azure Active Directoryную проверку подлинности. Дополнительные сведения см. в разделе:
- [Диалоговое окно входа SQL Server](../help-topics/sql-server-login-dialog.md)
- [Конфигурация универсального канала передачи данных (UDL)](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Примеры строк подключения
В этом разделе приведены примеры новых и существующих ключевых слов строки подключения для использования со `IDataInitialize::GetDataSource` свойством и `DBPROP_INIT_PROVIDERSTRING` .

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

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Встроенная проверка подлинности Windows с помощью интерфейса поставщика поддержки безопасности (SSPI)

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

### <a name="aad-username-and-password-authentication-using-adal"></a>Проверка подлинности имени пользователя и пароля AAD с помощью ADAL

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = ActiveDirectoryPassword**; Идентификатор пользователя = [username]; Password = [пароль]; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [сервер];D Аза данных = [база данных]; **Authentication = ActiveDirectoryPassword**; UID = [username]; PWD = [пароль]; Шифровать = да

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Встроенная проверка подлинности Azure Active Directory с помощью ADAL

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [сервер];D Аза данных = [база данных]; **Authentication = ActiveDirectoryIntegrated**; Шифровать = да

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Проверка подлинности Azure Active Directory с помощью маркера доступа

- Использование среды `IDataInitialize::GetDataSource`:
    > Provider = МСОЛЕДБСКЛ; Data Source = [сервер]; начальный каталог = [база данных]; **Маркер доступа = [маркер доступа]** ; Использовать шифрование для data = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Предоставление маркера доступа `DBPROP_INIT_PROVIDERSTRING` через не поддерживается

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
