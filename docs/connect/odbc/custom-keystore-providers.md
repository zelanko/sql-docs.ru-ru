---
title: Поставщики пользовательского хранилища ключей | Документация Майкрософт
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
caps.latest.revision: 1
ms.author: v-chojas
manager: craigg
author: MightyPen
ms.openlocfilehash: 613f8809003ba8f4501ea95371dedd44cff18a8d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "42786385"
---
# <a name="custom-keystore-providers"></a>Пользовательские поставщики хранилища ключей
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Обзор

Компонент шифрования столбца SQL Server 2016 требует шифрования ключей шифрования столбцов (ECEKs) на сервере быть получения клиентом и затем расшифрованы для ключей шифрования столбцов (ключей CEK) для доступа к данным, хранящихся в зашифрованных столбцах. ECEKs шифруются, главных ключей столбцов (ключей CMK), а безопасность CMK важно для обеспечения безопасности шифрования столбца. Таким образом CMK должны храниться в безопасном месте; Поставщик хранилища ключей шифрования столбцов предназначена для предоставления интерфейс, позволяющий драйвер ODBC для безопасного доступа к этим, сохранив ключей CMK. Для пользователей с их собственные защищенного хранилища интерфейс поставщика хранилища ключей Custom предоставляет платформу для реализации доступа к защищенным хранилища CMK для драйвера ODBC, который затем может использоваться для шифрования ключа шифрования Столбца и расшифровки.

Каждый поставщик хранилища ключей содержит и управляет один или несколько ключей CMK, которые идентифицируются по пути к ключам - строки формата, определенной поставщиком. Это, а также алгоритм шифрования, а также строку, определенной поставщиком, можно использовать для шифрования ключа шифрования Столбца и расшифровки ECEK. Алгоритм, а также ECEK и имя поставщика, хранятся в метаданных шифрования базы данных; см. в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) и [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) Дополнительные сведения. Таким образом являются две основные операции управления ключами:

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

где `CEKeystoreProvider_name` используется для идентификации конкретного столбца шифрования поставщик хранилища ключей (CEKeystoreProvider), и другие аргументы используются CEKeystoreProvider для шифрования и расшифровки ключа шифрования Столбца (E). Имя и keypath предоставляются метаданные CMK, хотя алгоритм и значение ECEK предоставленные метаданные ключа шифрования Столбца. Несколько поставщиков хранилища ключей могут присутствовать вместе с встроенные поставщики по умолчанию. При выполнении операции, требующей CEK драйвер использует метаданные CMK для поиска поставщика хранилища ключей соответствующий по имени и выполняет его операции расшифровки, который может быть выражен как:

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

Несмотря на то, что этот драйвер не шифруют ключи шифрования не требуется, средство управления ключами может потребоваться сделать это для реализации операций, таких как создание CMK и замену; для этого требуется выполнение обратной операцией:

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>Интерфейс CEKeyStoreProvider

В этом документе подробно описывается интерфейс CEKeyStoreProvider. Поставщик хранилища ключей, который реализует этот интерфейс можно использовать драйвер Microsoft ODBC для SQL Server. Исполнители CEKeyStoreProvider можно использовать в этом руководстве для разработки поставщиков пользовательского хранилища ключей можно использовать с помощью драйвера.

Библиотека поставщика хранилища ключей («Библиотека поставщика») — это библиотека динамической компоновки, который можно загрузить драйвер ODBC и содержит один или несколько поставщиков хранилища ключей. Символ `CEKeystoreProvider` необходимо экспортировать библиотеку поставщика, и быть адресом нулем массив указателей на `CEKeystoreProvider` структуры, по одному для каждого поставщика хранилища ключей в библиотеке.

Объект `CEKeystoreProvider` структура определяет точки входа поставщика одного хранилища ключей:

```
typedef struct CEKeystoreProvider {
    wchar_t *Name;
    int (*Init)(CEKEYSTORECONTEXT *ctx, errFunc *onError);
    int (*Read)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int *len);
    int (*Write)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len);
    int (*DecryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *ecek,
                        unsigned short ecekLen,
                        unsigned char **cekOut,
                        unsigned short *cekLen);
    int (*EncryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *cek,
                        unsigned short cekLen,
                        unsigned char **ecekOut,
                        unsigned short *ecekLen);
    void (*Free)();
} CEKEYSTOREPROVIDER;
```

|Имя поля|Описание|
|:--|:--|
|`Name`|Имя поставщика хранилища ключей. Он не должен быть таким же, как любой другой поставщик хранилища ключей, ранее загружены с помощью драйвера или присутствует в этой библиотеке. Завершающаяся нулем, расширенных-символ * строка.|
|`Init`|Функция инициализации. Если функцию не требуется, это поле может иметь значение null.|
|`Read`|Поставщик read-функция. Может иметь значение null, если не требуется.|
|`Write`|Функция записи поставщика. Требуется, если чтение не равно null. Может иметь значение null, если не требуется.|
|`DecryptCEK`|Функция расшифровки ECEK. Эта функция является причиной существования поставщик хранилища ключей и не может иметь значение null.|
|`EncryptCEK`|Функция шифрования ключа шифрования Столбца. Драйвер вызывает эту функцию, но она предоставляется для обеспечения программный доступ к ECEK создания средства управления ключами. Может иметь значение null, если не требуется.|
|`Free`|Функцию завершения. Может иметь значение null, если не требуется.|

За исключением Free, функции в этом интерфейсе все имеют пару параметров, **ctx** и **onError**. Первое из них определяет контекст, в котором функция вызывается, а второй — для отчетов об ошибках. См. в разделе [контекстов](#context-association) и [обработка ошибок](#error-handling) ниже дополнительные сведения.

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
Имя заполнителя для функции инициализации, определяемых поставщиком. Драйвер вызывает эту функцию один раз, после поставщика было загружено, но перед первым время, необходимое для выполнения расшифровать ECEK или Read()/Write() запросов. Эту функцию можно используйте для выполнения любой инициализации, которые необходимы. 

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`Return Value`|Возвращает ненулевое значение означает успех операции, или нуль, указывающее на ошибку.|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

Имя заполнителя для такой функции связи, определяемых поставщиком. Драйвер вызывает эту функцию, когда приложение запрашивает для чтения данных из (ранее записанных в) поставщик, использующий атрибут SQL_COPT_SS_CEKEYSTOREDATA соединения, что позволяет приложению считывать произвольные данные от поставщика. См. в разделе [взаимодействует с поставщиками хранилища ключей](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) Дополнительные сведения.

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`data`|[Выход] Указатель на буфер, в котором поставщик записывает данные для считывания приложением. Это соответствует полю данных CEKEYSTOREDATA структуры.|
|`len`|[Вход] Указатель на значение длины; При вводе, это максимальная длина буфера данных, а поставщик не должен записать более * len байт к нему. При возврате, необходимо обновить поставщик * len с количеством байтов, фактически записанных.|
|`Return Value`|Возвращает ненулевое значение означает успех операции, или нуль, указывающее на ошибку.|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
Имя заполнителя для такой функции связи, определяемых поставщиком. Драйвер вызывает эту функцию, когда приложение запрашивает для записи данных поставщика, используя атрибут подключения SQL_COPT_SS_CEKEYSTOREDATA записи произвольные данные к поставщику приложения. См. в разделе [взаимодействует с поставщиками хранилища ключей](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) Дополнительные сведения.

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`data`|[Вход] Указатель на буфер, содержащий данные для поставщика для чтения. Это соответствует полю данных CEKEYSTOREDATA структуры. Поставщик не должен считывать больше, чем длина байт из этого буфера.|
|`len`|[Вход] Число доступных байтов в данных. Это соответствует полю dataSize CEKEYSTOREDATA структуры.|
|`Return Value`|Возвращает ненулевое значение означает успех операции, или нуль, указывающее на ошибку.|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
Имя заполнителя для функции дешифрования ECEK определяемых поставщиком. Драйвер вызывает эту функцию для расшифровки зашифрованного CMK, связанные с этим поставщиком в ключ CEK ECEK.

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`keyPath`|[Вход] Значение [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) атрибут метаданных для CMK ссылается заданный ECEK. Завершающаяся нулем широкий-символ * строка. Это предназначено для определения CMK обрабатываемого этим поставщиком.|
|`alg`|[Вход] Значение [АЛГОРИТМ](../../t-sql/statements/create-column-encryption-key-transact-sql.md) атрибут метаданных для данного ECEK. Завершающаяся нулем широкий-символ * строка. Это предназначено для идентификации алгоритм шифрования, используемый для шифрования заданного ECEK.|
|`ecek`|[Вход] Указатель на ECEK, который нужно расшифровать.|
|`ecekLen`|[Вход] Длина ECEK.|
|`cekOut`|[Выход] Поставщик должен выделить память для расшифрованного ECEK и записать его адрес указателя, на которые указывают cekOut. Она должна существовать возможность освободить этот блок памяти с помощью [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) или свободная функция (Linux или Mac). Если нехватки памяти, выделенный из-за ошибки или иным образом, устанавливаются поставщик * cekOut на указатель null.|
|`cekLen`|[Выход] Поставщик должен записи адреса, на которые указывают cekLen длина расшифрованного ECEK, который был записан ** cekOut.|
|`Return Value`|Возвращает ненулевое значение означает успех операции, или нуль, указывающее на ошибку.|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
Имя заполнителя для функции определяемых поставщиком шифрования ключа шифрования Столбца. Драйвер не вызывайте эту функцию и не предоставляют свои функции через интерфейс ODBC, но чтобы разрешить программный доступ к созданию ECEK предоставляются средства управления ключами.

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`keyPath`|[Вход] Значение [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) атрибут метаданных для CMK ссылается заданный ECEK. Завершающаяся нулем широкий-символ * строка. Это предназначено для определения CMK обрабатываемого этим поставщиком.|
|`alg`|[Вход] Значение [АЛГОРИТМ](../../t-sql/statements/create-column-encryption-key-transact-sql.md) атрибут метаданных для данного ECEK. Завершающаяся нулем широкий-символ * строка. Это предназначено для идентификации алгоритм шифрования, используемый для шифрования заданного ECEK.|
|`cek`|[Вход] Указатель на ключ CEK, должны быть зашифрованы.|
|`cekLen`|[Вход] Длина ключа шифрования Столбца.|
|`ecekOut`|[Выход] Поставщик должен выделить память для зашифрованный ключ CEK и запись его адрес указатель, на которые указывают ecekOut. Она должна существовать возможность освободить этот блок памяти с помощью [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) или свободная функция (Linux или Mac). Если нехватки памяти, выделенный из-за ошибки или иным образом, устанавливаются поставщик * ecekOut на указатель null.|
|`ecekLen`|[Выход] Поставщик должен записи адреса, на которые указывают ecekLen длину зашифрованного ключа CEK, он был записан ** ecekOut.|
|`Return Value`|Возвращает ненулевое значение означает успех операции, или нуль, указывающее на ошибку.|

```
void (*Free)();
```
Имя заполнителя для поставщика определенную пользователем функцию завершения. Драйвер может вызвать эту функцию при нормальном завершении процесса.

> [!NOTE]
> *Строки расширенных символов — 2-байтовые символы (UTF-16) из-за как SQL Server сохраняет их.*


### <a name="error-handling"></a>Обработка ошибок

Как, возможно возникновение ошибок во время обработки поставщика, чтобы разрешить ему ошибки обратно драйверу подробнее чем логическое об успехе или сбое предоставляется механизм. Многие из функций иметь пару параметров, **ctx** и **onError**, которые используются совместно для этой цели в дополнение к успешной или неуспешной возвращаемое значение.

**Ctx** параметр определяет контекст, в котором происходит операция поставщика.

**OnError** параметр указывает на функцию отчетов об ошибках со следующим прототипом:

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|Аргумент|Описание|
|:--|:--|
|`ctx`|[Вход] Сообщить об ошибке на контекст.|
|`msg`|[Вход] Сообщение об ошибке для отчета. Завершающаяся нулем строку расширенных символов. На разрешение параметризованные данных должны присутствовать, эта строка может содержать форматирование insert последовательностей в форме, принимаемое [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) функции. Расширенные функции может быть указан в этом параметре, как описано ниже.|
|...|[Вход] Параметры дополнительных с переменным числом аргументов для подгонки описателей формата сообщений, соответствующим образом.|

Чтобы создать отчет, когда возникает ошибка, onError вызовы поставщика, указав параметр контекста передаваемые в функцию поставщика драйвером и сообщение об ошибке с необязательные дополнительные параметры для форматирования в нем. Поставщик может эта функция вызывается несколько раз для отправки сообщений об ошибках нумерацию вызов одного поставщика функции. Пример:

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


`msg` Параметр обычно представляет собой строку расширенных символов, но доступны дополнительные расширения:

Может использоваться с помощью одного из специальные предопределенные значения с помощью макроса IDS_MSG общих сообщений об ошибках уже существует и в виде localised в драйвере. Например, если поставщик не удается выделить память `IDS_S1_001` сообщение «Ошибка выделения памяти» можно использовать:

`onError(ctx, IDS_MSG(IDS_S1_001));`

Ошибки, опознается драйвером функция поставщика должен вернуть ошибку. Это выполняется в контексте операции ODBC, отправленной ошибок будет становятся доступными в дескриптор подключения или инструкцию через стандартный механизм диагностики ODBC (`SQLError`, `SQLGetDiagRec`, и `SQLGetDiagField`).


### <a name="context-association"></a>Контекст связи

`CEKEYSTORECONTEXT` Структуры, помимо предоставления контекста для ошибки обратного вызова, можно также использовать для определения контекста ODBC, в котором выполняется операция поставщика. Это позволяет поставщику для связывания данных для каждого из этих контекстов, например для реализации конфигурации подключения. С этой целью структура содержит 3 непрозрачные указатели, соответствующий контекст среды, подключения и инструкции:

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```
|Поле|Описание|
|:--|:--|
|`envCtx`|Контекст среды.|
|`dbcCtx`|Контекст соединения.|
|`stmtCtx`|Оператор контекста.|

Каждый из этих контекстов является непрозрачным значением, который, при который отличается от соответствующего дескриптор ODBC, можно использовать как уникальный идентификатор для дескриптора: если обрабатывать *X* связан с значение контекста *Y*, затем нет других дескрипторов среды, подключения или инструкцию которых существуют одновременно, в то же время, как *X* будет иметь значение контекста *Y*, и другие значения контекста не будут связаны с обрабатывать *X*. Если поставщик выполнены не хватает контекста определенного дескриптора, (например SQLSetConnectAttr вызовы для загрузки и настройка поставщиков, в которых есть не дескриптора инструкции) соответствующего значение контекста в структуре имеет значение null.


## <a name="example"></a>Пример

### <a name="keystore-provider"></a>Поставщик хранилища ключей

Следующий код является примером реализации поставщика хранилища ключей минимальным.

```
/* Custom Keystore Provider Example

Windows:   compile with cl MyKSP.c /LD /MD /link /out:MyKSP.dll
Linux/Mac: compile with gcc -fshort-wchar -fPIC -o MyKSP.so -shared MyKSP.c

 */

#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#endif

#include <stdlib.h>
#include <sqltypes.h>
#include "msodbcsql.h"
#include <sql.h>
#include <sqlext.h>

int __stdcall KeystoreInit(CEKEYSTORECONTEXT *ctx, errFunc *onError) {
    printf("KSP Init() function called\n");
    return 1;
}

static unsigned char *g_encryptKey;
static unsigned int g_encryptKeyLen;

int __stdcall KeystoreWrite(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len) {
    printf("KSP Write() function called (%d bytes)\n", len);
    if (len) {
        if (g_encryptKey)
            free(g_encryptKey);
        g_encryptKey = malloc(len);
        if (!g_encryptKey) {
            onError(ctx, L"Memory Allocation Error");
            return 0;
        }
        memcpy(g_encryptKey, data, len);
        g_encryptKeyLen = len;
    }
    return 1;
}

// Very simple "encryption" scheme - rotating XOR with the key
int __stdcall KeystoreDecrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg,
    unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen) {
    unsigned int i;
    printf("KSP Decrypt() function called (keypath=%S alg=%S ecekLen=%u)\n", keyPath, alg, ecekLen);
    if (wcscmp(keyPath, L"TheOneAndOnlyKey")) {
        onError(ctx, L"Invalid key path");
        return 0;
    }
    if (wcscmp(alg, L"none")) {
        onError(ctx, L"Invalid algorithm");
        return 0;
    }
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
#ifndef _WIN32
    *cekOut = malloc(ecekLen);
#else
    *cekOut = LocalAlloc(LMEM_FIXED, ecekLen);
#endif
    if (!*cekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *cekLen = ecekLen;
    for (i = 0; i < ecekLen; i++)
        (*cekOut)[i] = ecek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

// Note that in the provider interface, this function would be referenced via the CEKEYSTOREPROVIDER
// structure. However, that does not preclude keystore providers from exporting their own functions,
// as illustrated by this example where the encryption is performed via a separate function (with a
// different prototype than the one in the KSP interface.)
#ifdef _WIN32
__declspec(dllexport)
#endif
int KeystoreEncrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError,
    unsigned char *cek, unsigned short cekLen,
    unsigned char **ecekOut, unsigned short *ecekLen) {
    unsigned int i;
    printf("KSP Encrypt() function called (cekLen=%u)\n", cekLen);
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
    *ecekOut = malloc(cekLen);
    if (!*ecekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *ecekLen = cekLen;
    for (i = 0; i < cekLen; i++)
        (*ecekOut)[i] = cek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

CEKEYSTOREPROVIDER MyCustomKSPName_desc = {
    L"MyCustomKSPName",
    KeystoreInit,
    0,
    KeystoreWrite,
    KeystoreDecrypt,
    0
};

#ifdef _WIN32
__declspec(dllexport)
#endif
CEKEYSTOREPROVIDER *CEKeystoreProvider[] = {
    &MyCustomKSPName_desc,
    0
};
```

### <a name="odbc-application"></a>Приложения ODBC

Следующий код — это демонстрационное приложение, использующее выше поставщик хранилища ключей. При его, убедитесь, что библиотеки поставщика находится в том же каталоге, что двоичный файл приложения, и строка подключения указывает (или указывает имя источника данных, который содержит) `ColumnEncryption=Enabled` параметр.

```
/*
 Example application for demonstration of custom keystore provider usage

Windows:   compile with cl /MD kspapp.c /link odbc32.lib
Linux/Mac: compile with gcc -o kspapp -fshort-wchar kspapp.c -lodbc -ldl
 
 usage: kspapp connstr

 */

#define KSPNAME L"MyCustomKSPName"
#define PROV_ENCRYPT_KEY "JHKCWYT06N3RG98J0MBLG4E3"

#include <stdio.h>
#include <stdlib.h>
#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#include <dlfcn.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include "msodbcsql.h"

/* Convenience functions */

int checkRC(SQLRETURN rc, char *msg, int ret, SQLHANDLE h, SQLSMALLINT ht) {
    if (rc == SQL_ERROR) {
        fprintf(stderr, "Error occurred upon %s\n", msg);
        if (h) {
            SQLSMALLINT i = 0;
            SQLSMALLINT outlen = 0;
            char errmsg[1024];
            while ((rc = SQLGetDiagField(
                ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
                || rc == SQL_SUCCESS_WITH_INFO) {
                fprintf(stderr, "Err#%d: %s\n", i, errmsg);
            }
        }
        if (ret)
            exit(ret);
        return 0;
    }
    else if (rc == SQL_SUCCESS_WITH_INFO && h) {
        SQLSMALLINT i = 0;
        SQLSMALLINT outlen = 0;
        char errmsg[1024];
        printf("Success with info for %s:\n", msg);
        while ((rc = SQLGetDiagField(
            ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
            || rc == SQL_SUCCESS_WITH_INFO) {
            fprintf(stderr, "Msg#%d: %s\n", i, errmsg);
        }
    }
    return 1;
}

void postKspError(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...) {
    if (msg > (wchar_t*)65535)
        wprintf(L"Provider emitted message: %s\n", msg);
    else
        wprintf(L"Provider emitted message ID %d\n", msg);
}

int main(int argc, char **argv) {
    char sqlbuf[1024];
    SQLHENV env;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLRETURN rc;
    unsigned char CEK[32];
    unsigned char *ECEK;
    unsigned short ECEKlen;
#ifdef _WIN32
    HMODULE hProvLib;
#else
    void *hProvLib;
#endif
    CEKEYSTORECONTEXT ctx = {0};
    CEKEYSTOREPROVIDER **ppKsp, *pKsp;
    int(__stdcall *pEncryptCEK)(CEKEYSTORECONTEXT *, errFunc *, unsigned char *, unsigned short, unsigned char **, unsigned short *);
    int i;
    if (argc < 2) {
        fprintf(stderr, "usage: kspapp connstr\n");
        return 1;
    }

    /* Load the provider library */
#ifdef _WIN32
    if (!(hProvLib = LoadLibrary("MyKSP.dll"))) {
#else
    if (!(hProvLib = dlopen("./MyKSP.so", RTLD_NOW))) {
#endif
        fprintf(stderr, "Error loading KSP library\n");
        return 2;
    }
#ifdef _WIN32
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)GetProcAddress(hProvLib, "CEKeystoreProvider"))) {
#else
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)dlsym(hProvLib, "CEKeystoreProvider"))) {
#endif
        fprintf(stderr, "The export CEKeystoreProvider was not found in the KSP library\n");
        return 3;
    }
    while (pKsp = *ppKsp++) {
        if (!memcmp(KSPNAME, pKsp->Name, sizeof(KSPNAME)))
            goto FoundProv;
    }
    fprintf(stderr, "Could not find provider in the library\n");
    return 4;
FoundProv:
    if (pKsp->Init && !pKsp->Init(&ctx, postKspError)) {
        fprintf(stderr, "Could not initialize provider\n");
        return 5;
    }
#ifdef _WIN32
    if (!(pEncryptCEK = (LPVOID)GetProcAddress(hProvLib, "KeystoreEncrypt"))) {
#else
    if (!(pEncryptCEK = dlsym(hProvLib, "KeystoreEncrypt"))) {
#endif
        fprintf(stderr, "The export KeystoreEncrypt was not found in the KSP library\n");
        return 6;
    }
    if (!pKsp->Write) {
        fprintf(stderr, "Provider does not support configuration\n");
        return 7;
    }

    /* Configure the provider with the key */
    if (!pKsp->Write(&ctx, postKspError, PROV_ENCRYPT_KEY, strlen(PROV_ENCRYPT_KEY))) {
        fprintf(stderr, "Error writing to KSP\n");
        return 8;
    }

    /* Generate a CEK and encrypt it with the provider */
    srand(time(0) ^ getpid());
    for (i = 0; i < sizeof(CEK); i++)
        CEK[i] = rand();

    if (!pEncryptCEK(&ctx, postKspError, CEK, sizeof(CEK), &ECEK, &ECEKlen)) {
        fprintf(stderr, "Error encrypting CEK\n");
        return 9;
    }

    /* Connect to Server */
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &env);
    checkRC(rc, "allocating environment handle", 2, 0, 0);
    rc = SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0);
    checkRC(rc, "setting ODBC version to 3.0", 3, env, SQL_HANDLE_ENV);
    rc = SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc);
    checkRC(rc, "allocating connection handle", 4, env, SQL_HANDLE_ENV);
    rc = SQLDriverConnect(dbc, 0, argv[1], strlen(argv[1]), NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    checkRC(rc, "connecting to data source", 5, dbc, SQL_HANDLE_DBC);
    rc = SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
    checkRC(rc, "allocating statement handle", 6, dbc, SQL_HANDLE_DBC);

    /* Create a CMK definition on the server */
    {
        static char cmkSql[] = "CREATE COLUMN MASTER KEY CustomCMK WITH ("
            "KEY_STORE_PROVIDER_NAME = 'MyCustomKSPName',"
            "KEY_PATH = 'TheOneAndOnlyKey')";
        printf("Create CMK: %s\n", cmkSql);
        SQLExecDirect(stmt, cmkSql, SQL_NTS);
    }

    /* Create a CEK definition on the server */
    {
        const char cekSqlBefore[] = "CREATE COLUMN ENCRYPTION KEY CustomCEK WITH VALUES ("
            "COLUMN_MASTER_KEY = CustomCMK,"
            "ALGORITHM = 'none',"
            "ENCRYPTED_VALUE = 0x";
        char *cekSql = malloc(sizeof(cekSqlBefore) + 2 * ECEKlen + 2); /* 1 for ')', 1 for null terminator */
        strcpy(cekSql, cekSqlBefore);
        for (i = 0; i < ECEKlen; i++)
            sprintf(cekSql + sizeof(cekSqlBefore) - 1 + 2 * i, "%02x", ECEK[i]);
        strcat(cekSql, ")");
        printf("Create CEK: %s\n", cekSql);
        SQLExecDirect(stmt, cekSql, SQL_NTS);
        free(cekSql);
#ifdef _WIN32
        LocalFree(ECEK);
#else
        free(ECEK);
#endif
    }

#ifdef _WIN32
    FreeLibrary(hProvLib);
#else
    dlclose(hProvLib);
#endif

    /* Create a table with encrypted columns */
    {
        static char *tableSql = "CREATE TABLE CustomKSPTestTable ("
            "c1 int,"
            "c2 varchar(255) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = CustomCEK, ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'))";
        printf("Create table: %s\n", tableSql);
        SQLExecDirect(stmt, tableSql, SQL_NTS);
    }

    /* Load provider into the ODBC Driver and configure it */
    {
        unsigned char ksd[sizeof(CEKEYSTOREDATA) + sizeof(PROV_ENCRYPT_KEY) - 1];
        CEKEYSTOREDATA *pKsd = (CEKEYSTOREDATA*)ksd;
        pKsd->name = L"MyCustomKSPName";
        pKsd->dataSize = sizeof(PROV_ENCRYPT_KEY) - 1;
        memcpy(pKsd->data, PROV_ENCRYPT_KEY, sizeof(PROV_ENCRYPT_KEY) - 1);
#ifdef _WIN32
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "MyKSP.dll", SQL_NTS);
#else
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "./MyKSP.so", SQL_NTS);
#endif
        checkRC(rc, "Loading KSP into ODBC Driver", 7, dbc, SQL_HANDLE_DBC);
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREDATA, (SQLPOINTER)pKsd, SQL_IS_POINTER);
        checkRC(rc, "Configuring the KSP", 7, dbc, SQL_HANDLE_DBC);
    }

    /* Insert some data */
    {
        int c1;
        char c2[256];
        rc = SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &c1, 0, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        rc = SQLBindParameter(stmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_VARCHAR, 255, 0, c2, 255, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        for (i = 0; i < 10; i++) {
            c1 = i * 10 + i + 1;
            sprintf(c2, "Sample data %d for column 2", i);
            rc = SQLExecDirect(stmt, "INSERT INTO CustomKSPTestTable (c1, c2) values (?, ?)", SQL_NTS);
            checkRC(rc, "Inserting rows query", 10, stmt, SQL_HANDLE_STMT);
        }
        printf("(Encrypted) data has been inserted into the [CustomKSPTestTable]. You may inspect the data now.\n"
            "Press Enter to continue...\n");
        getchar();
    }

    /* Retrieve the data */
    {
        int c1;
        char c2[256];
        rc = SQLBindCol(stmt, 1, SQL_C_LONG, &c1, 0, 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLBindCol(stmt, 2, SQL_C_CHAR, c2, sizeof(c2), 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLExecDirect(stmt, "SELECT c1, c2 FROM CustomKSPTestTable", SQL_NTS);
        checkRC(rc, "Retrieving rows query", 12, stmt, SQL_HANDLE_STMT);
        while (SQL_SUCCESS == (rc = SQLFetch(stmt)))
            printf("Retrieved data: c1=%d c2=%s\n", c1, c2);
        SQLFreeStmt(stmt, SQL_CLOSE);
        printf("Press Enter to clean up and exit...\n");
        getchar();
    }

    /* Clean up */
    {
        SQLExecDirect(stmt, "DROP TABLE CustomKSPTestTable", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN ENCRYPTION KEY CustomCEK", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN MASTER KEY CustomCMK", SQL_NTS);
        printf("Removed table, CEK, and CMK\n");
    }
    SQLDisconnect(dbc);
    SQLFreeHandle(SQL_HANDLE_DBC, dbc);
    SQLFreeHandle(SQL_HANDLE_ENV, env);
    return 0;
}

```

## <a name="see-also"></a>См. также:

[Использование функции Always Encrypted с драйвером ODBC](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
