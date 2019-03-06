---
title: С помощью Azure Active Directory | Документация по Microsoft для SQL Server
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
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744861"
---
# <a name="using-azure-active-directory"></a>Использование Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Назначение

Начиная с версии 18.2.1, драйвер Microsoft OLE DB для SQL Server позволяет приложениям OLE DB для подключения к экземпляру базы данных SQL Azure с помощью федеративного удостоверения. Новые методы проверки подлинности:
- Azure Active Directory идентификатор входа и пароль
- Маркер доступа Azure Active Directory
- Интегрированная проверка подлинности Azure Active Directory
- Идентификатор имени входа SQL и пароля

> [!NOTE]  
> При использовании следующих параметров Azure Active Directory с помощью драйвера OLE DB, убедитесь, что [Active Directory Authentication Library для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) установки:
> - Azure Active Directory идентификатор входа и пароль
> - Интегрированная проверка подлинности Azure Active Directory
>
> ADAL не требуется для других методов проверки подлинности или операций OLE DB.

> [!NOTE]
> Следующие режимы проверки подлинности с помощью `DataTypeCompatibility` (или его соответствующие свойства) присвоено `80` — **не** поддерживается:
> - Аутентификация Azure Active Directory, используя идентификатор входа и пароль
> - Аутентификация Azure Active Directory, используя маркер доступа
> - Интегрированная проверка подлинности Azure Active Directory

## <a name="connection-string-keywords-and-properties"></a>Ключевые слова строки подключения и свойств
Для поддержки проверки подлинности Azure Active Directory были введены следующие ключевые слова строки подключения:

|Ключевое слово строки подключения|Свойства подключения|Описание|
|---               |---                |---        |
|Маркер доступа|SSPROP_AUTH_ACCESS_TOKEN|Указывает маркер доступа для проверки подлинности в Azure Active Directory. |
|Проверка подлинности|SSPROP_AUTH_MODE|Указывает метод проверки подлинности.|

Дополнительные сведения о новых ключевых слов и свойствах см. следующие страницы:
- [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Свойства инициализации и авторизации](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Шифрование и проверку сертификатов
В этом разделе описываются изменения шифрования и поведение проверки сертификата. Эти изменения будут **только** вступают в силу при использовании новой проверки подлинности или токен доступа ключевых слов строки подключения (или их соответствующие свойства).

### <a name="encryption"></a>Шифрование
Для повышения безопасности, когда новые подключения свойства/ключевые слова используются драйвер переопределяет значение по умолчанию шифрования при установке для него `yes`. Переопределение происходит во время инициализации объекта источника данных. Если шифрование задается до инициализации любыми средствами, значение соблюдаться и не переопределен.

> [!NOTE]   
> В приложениях ADO, а также в приложениях, которые извлекают `IDBInitialize` интерфейс, с помощью `IDataInitialize::GetDataSource`, основной компонент, реализующий интерфейс явно задается значение по умолчанию `no`. Таким образом, новые проверки подлинности свойства/ключевые слова использовать этот параметр и значение шифрования **не** переопределении. Таким образом, **рекомендуется** , эти приложения явно задать `Use Encryption for Data=true` переопределить значение по умолчанию.

### <a name="certificate-validation"></a>Проверка сертификатов
Для повышения безопасности учитывают новые подключения свойства/ключевые слова `TrustServerCertificate` параметр (и его соответствующие свойства строки подключения ключевые слова /) **независимо от параметра шифрования клиента**. Таким образом проверить сертификат сервера по умолчанию.

> [!NOTE]   
> Проверку сертификата можно также управлять с помощью `Value` поле `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` запись реестра. Допустимые значения: `0` или `1`. Драйвер OLE DB выбирает наиболее безопасный вариант между реестром и ключевое слово property параметры подключения. То есть драйвер будет проверять сертификат сервера до тех пор, пока по крайней мере один из параметров реестра и подключению включает проверку сертификата сервера.

## <a name="gui-additions"></a>Дополнения графического пользовательского интерфейса
Драйвер графического пользовательского интерфейса был улучшен для обеспечения проверки подлинности Azure Active Directory. Дополнительные сведения см. в разделе:
- [Диалоговое окно входа SQL Server](../help-topics/sql-server-login-dialog.md)
- [Настройка ссылок (UDL) Universal Data](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Примеры строк подключения
В этом разделе показаны примеры подключение новых и существующих ключевых слов строки для использования с `IDataInitialize::GetDataSource` и `DBPROP_INIT_PROVIDERSTRING` свойство.

### <a name="sql-authentication"></a>Проверка подлинности SQL
- Использование среды `IDataInitialize::GetDataSource`:
    - Добавления:
        > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Проверки подлинности = SqlPassword**; Идентификатор пользователя = [username]; Пароль = [пароль]; Использовать шифрование данных = true
    - Устарело:
        > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; Идентификатор пользователя = [username]; Пароль = [пароль]; Использовать шифрование данных = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    - Добавления:
        > Server = [server]; Database = [база данных]; **Проверки подлинности = SqlPassword**; UID = [username]; PWD = [пароль]; Шифрование = yes
    - Устарело:
        > Server = [server]; Database = [база данных]; UID = [username]; PWD = [пароль]; Шифрование = yes

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Встроенная проверка подлинности Windows, с помощью интерфейса поставщика поддержки безопасности (SSPI)

- Использование среды `IDataInitialize::GetDataSource`:
    - Добавления:
        > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Проверки подлинности = ActiveDirectoryIntegrated**; Использовать шифрование данных = true
    - Устарело:
        > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Встроенная система безопасности = SSPI**; Использовать шифрование данных = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    - Добавления:
        > Server = [server]; Database = [база данных]; **Проверки подлинности = ActiveDirectoryIntegrated**; Шифрование = yes
    - Устарело:
        > Server = [server]; Database = [база данных]; **Trusted_Connection = yes**; Шифрование = yes

### <a name="aad-username-and-password-authentication-using-adal"></a>Имя пользователя и пароль аутентификацию AAD с помощью ADAL

- Использование среды `IDataInitialize::GetDataSource`:
    > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Проверки подлинности = ActiveDirectoryPassword**; Идентификатор пользователя = [username]; Пароль = [пароль]; Использовать шифрование данных = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [server]; Database = [база данных]; **Проверки подлинности = ActiveDirectoryPassword**; UID = [username]; PWD = [пароль]; Шифрование = yes

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Встроенная проверка подлинности Azure Active Directory, с помощью ADAL

- Использование среды `IDataInitialize::GetDataSource`:
    > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Проверки подлинности = ActiveDirectoryIntegrated**; Использовать шифрование данных = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [server]; Database = [база данных]; **Проверки подлинности = ActiveDirectoryIntegrated**; Шифрование = yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Аутентификация Azure Active Directory, с помощью маркера доступа

- Использование среды `IDataInitialize::GetDataSource`:
    > Поставщик = MSOLEDBSQL; источник данных = [server]; Initial Catalog = [база данных]; **Токена доступа = [маркер доступа]**; Использовать шифрование данных = true
- Использование среды `DBPROP_INIT_PROVIDERSTRING`:
    > Предоставляя маркер доступа через `DBPROP_INIT_PROVIDERSTRING` не поддерживается

## <a name="code-samples"></a>Примеры кода

В следующих примерах показано код, необходимый для подключения к Azure Active Directory с помощью ключевых слов подключения. 

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
- [Авторизация доступа к веб-приложениям Azure Active Directory, используя поток предоставления кода OAuth 2.0](https://go.microsoft.com/fwlink/?linkid=2072672).

- Ознакомьтесь со сведениями о [проверке подлинности Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2073783) для SQL Server.

- Настройка подключений драйвера, с помощью [ключевых слов строки подключения](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) поддерживает драйвер OLE DB.
