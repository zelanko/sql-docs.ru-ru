---
title: "Поставщики пользовательских ключей | Документы Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
caps.latest.revision: 1
ms.author: v-chojas
manager: jhubbard
author: MightyPen
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd6d86df2ec743376af34ac93d8b746bbe0a6eb3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="custom-keystore-providers"></a>Поставщики пользовательского хранилища ключей
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Обзор

Средства шифрования столбца SQL Server 2016 требует шифрования ключей шифрования столбцов (ECEKs) хранятся на сервере быть получения клиентом и дешифрован ключей шифрования столбца (столбца) для доступа к данным, хранящиеся в зашифрованных столбцах. ECEKs шифруются по главных ключей столбцов (ключей CMK) и безопасность CMK важно для обеспечения безопасности шифрования столбца. Таким образом CMK должен храниться в безопасном месте; Поставщик хранилища ключей шифрования столбцов предназначена для предоставления интерфейс, позволяющий драйвер ODBC для доступа к этим безопасно хранятся ключей CMK. Для пользователей с их собственных безопасного хранения интерфейс поставщика хранилища ключей настраиваемый предоставляет платформу для реализации доступа к защищенным хранилища CMK для драйвера ODBC, который можно использовать для выполнения CEK шифрования и расшифровки.

Каждый поставщик хранилища ключей содержит и управляет один или несколько ключей CMK, которые идентифицируются по путей - строк формата, определенной поставщиком. Это, вместе с алгоритм шифрования, а также строки, определенной поставщиком, можно использовать для выполнения шифрования ключа CEK и расшифровка ECEK. Алгоритм, а также ECEK и имя поставщика, хранятся в метаданных шифрования базы данных; в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) и [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) для получения дополнительной информации. Таким образом являются двумя основными операциями управления ключами:

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

где `CEKeystoreProvider_name` используется для идентификации определенного столбца шифрования поставщик хранилища ключей (CEKeystoreProvider) и другие аргументы используются CEKeystoreProvider для шифрования и расшифровки CEK (E). Имя и keypath обеспечиваются с помощью метаданных CMK, пока алгоритма и ECEK значение обеспечиваются CEK метаданных. Наряду с встроенные поставщики по умолчанию может присутствовать несколько поставщиков хранилища ключей. При выполнении операции, требующей CEK драйвер использует метаданные CMK поиск поставщика хранилища ключей соответствующий по имени и выполняет его операции расшифровки, который может быть выражен как:

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

Несмотря на то что драйвер шифрования столбца не требуется, средство управления ключами может потребоваться сделать это для реализации операции, такие как создание CMK и поворота; Это требует выполнения обратной операции:

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>Интерфейс CEKeyStoreProvider

В этом документе подробно описываются CEKeyStoreProvider интерфейса. Поставщик хранилища ключей, который реализует этот интерфейс можно использовать драйвер Microsoft ODBC для SQL Server. Исполнители CEKeyStoreProvider можно использовать это руководство для разработки поставщиков пользовательского хранилища ключей можно использовать драйвер.

Библиотека поставщика хранилища ключей («Библиотека поставщика») является динамическая библиотека, которая может загружаться драйвером ODBC и содержит один или несколько поставщиков хранилища ключей. Символ `CEKeystoreProvider` необходимо экспортировать в библиотеке поставщика и адрес нулем массив указателей на `CEKeystoreProvider` структуры, по одному для каждого поставщика хранилища ключей в библиотеке.

Объект `CEKeystoreProvider` структура определяет поставщика хранилища ключей одной точки входа:

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

|Имя поля|Description|
|:--|:--|
|`Name`|Имя поставщика хранилища ключей. Он не должен быть таким же, как любой другой поставщик хранилища ключей, ранее загруженного драйвером или присутствует в этой библиотеке. Нули, расширенный-символ * строки.|
|`Init`|Функцию инициализации. Если функции инициализации не является обязательным, это поле может иметь значение null.|
|`Read`|Функция read поставщика. Может принимать значение null, если не требуется.|
|`Write`|Функция записи поставщика. Требуется, если чтения не равно null. Может принимать значение null, если не требуется.|
|`DecryptCEK`|Функция ECEK расшифровки. Эта функция является причиной существование поставщик хранилища ключей и не может иметь значение null.|
|`EncryptCEK`|Функция шифрования ключа CEK. Драйвер вызывает эту функцию, но она предназначена для обеспечения программный доступ к созданию ECEK средствами управления ключами. Может принимать значение null, если не требуется.|
|`Free`|Функцию завершения. Может принимать значение null, если не требуется.|

За исключением Free, функции в этом интерфейсе все имеют пару параметров, **ctx** и **onError**. Первый интерфейс определяет контекст, в котором функция вызывается, то время как второй используется для сообщения об ошибках. В разделе [контексты](#context-association) и [обработка ошибок](#error-handling) ниже для получения дополнительной информации.

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
Именем-заполнителем для функции инициализации, определяемых поставщиком. Драйвер вызывает эту функцию один раз, после поставщика была загружена, но перед первым запрашивает время, необходимое для выполнения расшифровать ECEK или Read()/Write(). Эту функцию можно используйте для выполнения любой инициализации, которые необходимы. 

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`Return Value`|Возвращает ненулевое значение, указывающее на успех или нулевое значение, указывающее на неудачу.|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

Именем-заполнителем для такой функции связи, определенное поставщиком. Драйвер вызывает эту функцию при запросе приложением для чтения данных из (ранее записанных в) поставщика с помощью атрибута соединения SQL_COPT_SS_CEKEYSTOREDATA, что позволяет приложению считывать произвольных данных от поставщика. В разделе [обмена данными с помощью поставщиков хранилища ключей](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) для получения дополнительной информации.

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`data`|[Выход] Указатель на буфер, в котором поставщик записывает данные для считывания приложением. Это соответствует полю данных CEKEYSTOREDATA структуры.|
|`len`|[Вход] Указатель на значение длины; После ввода данных, это максимальная длина буфера данных, и поставщик не должен записать более * len байт к нему. По возвращении у поставщика обновление * len число фактически записанных байт.|
|`Return Value`|Возвращает ненулевое значение, указывающее на успех или нулевое значение, указывающее на неудачу.|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
Именем-заполнителем для такой функции связи, определенное поставщиком. Драйвер вызывает эту функцию при запросе приложением для записи данных поставщика, с помощью атрибута соединения SQL_COPT_SS_CEKEYSTOREDATA, написать произвольных данных к поставщику приложения. В разделе [обмена данными с помощью поставщиков хранилища ключей](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) для получения дополнительной информации.

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`data`|[Вход] Указатель на буфер, содержащий данные для поставщика для чтения. Это соответствует полю данных CEKEYSTOREDATA структуры. Поставщик не должны считать более чем len байт из этого буфера.|
|`len`|[Вход] Число байтов, доступных в данных. Это соответствует полю dataSize CEKEYSTOREDATA структуры.|
|`Return Value`|Возвращает ненулевое значение, указывающее на успех или нулевое значение, указывающее на неудачу.|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
Именем-заполнителем для функции дешифрования ECEK определенное поставщиком. Драйвер вызывает эту функцию, чтобы расшифровать ECEK шифруется Главным, связанные с этим поставщиком в ключа CEK.

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`keyPath`|[Вход] Значение [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) атрибут метаданных для ссылается данный ECEK CMK. Нули широкий-символ * строки. Этот способ предназначен для определения CMK, обрабатываемых этим поставщиком.|
|`alg`|[Вход] Значение [АЛГОРИТМ](../../t-sql/statements/create-column-encryption-key-transact-sql.md) атрибут метаданных для данного ECEK. Нули широкий-символ * строки. Этот способ предназначен для определения алгоритма шифрования, используемого для шифрования данного ECEK.|
|`ecek`|[Вход] Указатель на ECEK для расшифровки.|
|`ecekLen`|[Вход] Длина ECEK.|
|`cekOut`|[Выход] Поставщик должен выделить память для расшифрованного ECEK и записи его адрес указатель, который указывает cekOut. Ее можно освободить этот блок памяти с помощью [LocalFree](https://msdn.microsoft.com/library/windows/desktop/aa366730(v=vs.85).aspx) (Windows) или освобождения (Linux или Mac) функции. Если памяти не выделенные из-за ошибки или иным образом, поставщик устанавливаются * cekOut на указатель null.|
|`cekLen`|[Выход] Поставщик должен записи адреса, на который указывает cekLen длина расшифрованного ECEK, который внес в ** cekOut.|
|`Return Value`|Возвращает ненулевое значение, указывающее на успех или нулевое значение, указывающее на неудачу.|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
Именем-заполнителем для функции определен поставщик шифрования CEK. Драйвер не вызывайте эту функцию и не предоставлять свои функции через интерфейс ODBC, но она предназначена для обеспечения программный доступ к созданию ECEK средствами управления ключами.

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Контекст операции.|
|`onError`|[Вход] Функция отчетов об ошибках.|
|`keyPath`|[Вход] Значение [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) атрибут метаданных для ссылается данный ECEK CMK. Нули широкий-символ * строки. Этот способ предназначен для определения CMK, обрабатываемых этим поставщиком.|
|`alg`|[Вход] Значение [АЛГОРИТМ](../../t-sql/statements/create-column-encryption-key-transact-sql.md) атрибут метаданных для данного ECEK. Нули широкий-символ * строки. Этот способ предназначен для определения алгоритма шифрования, используемого для шифрования данного ECEK.|
|`cek`|[Вход] Указатель для шифрования ключа CEK.|
|`cekLen`|[Вход] Длина ключа CEK.|
|`ecekOut`|[Выход] Поставщик должен выделить память для зашифрованный CEK и записи его адрес указатель, который указывает ecekOut. Ее можно освободить этот блок памяти с помощью [LocalFree](https://msdn.microsoft.com/library/windows/desktop/aa366730(v=vs.85).aspx) (Windows) или освобождения (Linux или Mac) функции. Если памяти не выделенные из-за ошибки или иным образом, поставщик устанавливаются * ecekOut на указатель null.|
|`ecekLen`|[Выход] Поставщик должен записи адреса, на который указывает ecekLen длину зашифрованного ключа CEK, записала во ** ecekOut.|
|`Return Value`|Возвращает ненулевое значение, указывающее на успех или нулевое значение, указывающее на неудачу.|

```
void (*Free)();
```
Именем-заполнителем для поставщика определенную пользователем функцию завершения. Драйвер может вызвать эту функцию при нормальном завершении процесса.

> [!NOTE]
> *Строки расширенных символов, 2-байтовые знаки (UTF-16) из-за как SQL Server сохраняет их.*


### <a name="error-handling"></a>Обработка ошибок

Как, возможно возникновение ошибок во время обработки поставщика, механизм предоставляется позволяет сообщать об ошибках к драйверу в более конкретные подробные сведения, чем логическое успешных завершений и сбоев. Многие функции иметь пару параметров, **ctx** и **onError**, который используются совместно для этой цели в дополнение к возвращаемое значение успешных завершений и сбоев.

**Ctx** параметр определяет контекст, в котором осуществляется работы поставщика.

**OnError** параметр указывает на функцию отчетов об ошибках со следующим прототипом:

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|Аргумент|Description|
|:--|:--|
|`ctx`|[Вход] Отчет об ошибке на контекст.|
|`msg`|[Вход] Сообщение об ошибке, в отчет. Символом NULL строку расширенных символов. Чтобы параметризованные сведения должны присутствовать, эта строка может содержать последовательности форматирования вставки формы, принимаемое [FormatMessage](https://msdn.microsoft.com/library/windows/desktop/ms679351(v=vs.85).aspx) функции. Расширенные функции может быть указан в этом параметре, как описано ниже.|
|...|[Вход] Параметры дополнительных с переменным числом аргументов для размещения описатели формата в сообщение, соответствующим образом.|

Чтобы создать отчет, когда возникает ошибка, onError вызовы поставщика, указав параметр контекста передан в функцию поставщика драйвером и сообщение об ошибке с необязательные дополнительные параметры для форматирования в нем. Поставщик может вызвать эту функцию несколько раз для учета нескольких сообщения об ошибках последовательно в рамках вызова функция одного поставщика. Например:

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


`msg` Обычно представляет собой строку расширенных символов, но доступны дополнительные расширения:

Может использоваться с помощью одного из специальных предопределенных значений с помощью макроса IDS_MSG общие сообщения об ошибке уже существует и в форме localised в драйвере. Например, если поставщик не удается выделить память `IDS_S1_001` сообщение «Ошибка при выделении памяти» можно использовать:

`onError(ctx, IDS_MSG(IDS_S1_001));`

Для ошибок распознано драйвером функция поставщика должен возвращать сбоя. Это выполняется в контексте операции ODBC, отправленное ошибки будет становятся доступными для дескриптора соединения или инструкция через стандартный механизм диагностики ODBC (`SQLError`, `SQLGetDiagRec`, и `SQLGetDiagField`).


### <a name="context-association"></a>Контекст ассоциации

`CEKEYSTORECONTEXT` Структуры, помимо контекста для ошибки обратного вызова, может также использоваться для определения контекста ODBC, в котором выполняется операция поставщика. Это позволит поставщику для связывания данных для каждого из этих контекстов, например для реализации конфигурации для подключения. С этой целью структура содержит 3 непрозрачные указатели, соответствующий контекст среды, инструкции и соединения:

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```
|Поле|Description|
|:--|:--|
|`envCtx`|Контекст среды.|
|`dbcCtx`|Контекст соединения.|
|`stmtCtx`|Оператор контекста.|

Каждый из этих контекстов является непрозрачным значением, который при не таким, как соответствующий дескриптор ODBC, используется как уникальный идентификатор для дескриптора: если обрабатывать *X* связан с значение контекста *Y*, затем нет других дескрипторов среды, соединение или оператор которых существуют одновременно, в то же время, как *X* будет иметь значение контекста *Y*, и другие значения контекста будет связан с обрабатывать *X*. Если нет выполнить операцию поставщика контекст определенного дескриптора (например SQLSetConnectAttr вызовы для загрузки и настройка поставщиков, в которых нет ни один дескриптор инструкции) соответствующее значение контекста в структуре имеет значение null.


## <a name="example"></a>Пример

### <a name="keystore-provider"></a>Поставщик хранилища ключей

Следующий код является примером реализации поставщика хранилища ключей минимальной.

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

Следующий код является демонстрационного приложения, использующего выше поставщик хранилища ключей. При запуске, обеспечить библиотеки поставщика в том же каталоге, как двоичный файл приложения, и что строка подключения указывает (или задает имя источника данных, который содержит) `ColumnEncryption=Enabled` параметр.

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

[Использование постоянного шифрования с драйвером ODBC](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)

