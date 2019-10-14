---
title: Использование классификации данных с Microsoft ODBC Driver for SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 07/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: 8f0f821890cabe25a9abb572e453c9846c75ec94
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041129"
---
# <a name="data-classification"></a>Классификация данных
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Обзор
В целях управления конфиденциальными данными SQL Server и Azure SQL Server представил возможность предоставлять столбцы базы данных с метаданными чувствительности, которые позволяют клиентскому приложению работать с различными типами конфиденциальных данных (например, Health, финансовая и т. д.). ) в соответствии с политиками защиты данных.

Дополнительные сведения о назначении классификации столбцам см. в разделе [Обнаружение и классификация данных SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017).

Microsoft ODBC Driver 17,2 позволяет получать эти метаданные через SQLGetDescField, используя идентификатор поля SQL_CA_SS_DATA_CLASSIFICATION.

## <a name="format"></a>Формат
SQLGetDescField имеет следующий синтаксис:

```  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```
*дескрипторхандле*  
 Входной Дескриптор IRD (дескриптор строки реализации). Можно получить с помощью вызова SQLGetStmtAttr с атрибутом инструкции SQL_ATTR_IMP_ROW_DESC
  
 *рекнумбер*  
 [Вход] 0
  
 *фиелдидентифиер*  
 Входной SQL_CA_SS_DATA_CLASSIFICATION
  
 *ValuePtr*  
 Проверки Выходной буфер
  
 *BufferLength*  
 Входной Длина выходного буфера в байтах

 *Стрингленгсптр* [Output] указатель на буфер, в котором возвращается общее число байт, доступных для возврата в *ValuePtr*.
 
> [!NOTE]
> Если размер буфера неизвестен, его можно определить, вызвав SQLGetDescField с *ValuePtr* как NULL и проверив значение *стрингленгсптр*.
 
Если сведения о классификации данных недоступны, будет возвращено *недопустимое поле дескриптора* .

При успешном вызове SQLGetDescField буфер, на который указывает *ValuePtr* , будет содержать следующие данные:

 `nn nn [n sensitivitylabels] tt tt [t informationtypes] cc cc [c columnsensitivitys]`

> [!NOTE]
> `nn nn`, `tt tt` и `cc cc` — многобайтовые целые числа, которые хранятся с наименьшим значащим байтом по нижнему адресу.

*`sensitivitylabel`* и *`informationtype`* являются обеими формами

 `nn [n bytes name] ii [i bytes id]`

*`columnsensitivity`* имеет вид

 `nn nn [n sensitivityprops]`

Для каждого столбца *(c)* имеются *n* 4 байта *`sensitivityprops`* :

 `ss ss tt tt`

s-index в массив *`sensitivitylabels`* `FF FF`, если он не помечен

t-индекс в массиве *`informationtypes`* `FF FF`, если он не помечен


<br><br>
Формат данных может выражаться в следующих псевдо-структурах:

```
struct IDnamePair {
 BYTE nameLen;
 USHORT name[nameLen];
 BYTE idLen;
 USHORT id[idLen];
};

struct SensitivityProp {
 USHORT labelIdx;
 USHORT infoTypeIdx;
};

USHORT nLabels;
struct IDnamePair labels[nLabels];
USHORT nInfoTypes;
struct IDnamePair infotypes[nInfoTypes];
USHORT nColumns;
struct {
 USHORT nProps;
 struct SensitivityProp[nProps];
} columnClassification[nColumns];
```


## <a name="code-sample"></a>Пример кода
Тестовое приложение, которое показывает, как считывать метаданные классификации данных. В Windows его можно скомпилировать с помощью `cl /MD dataclassification.c /I (directory of msodbcsql.h) /link odbc32.lib` и выполнить со строкой подключения, а SQL-запрос (который возвращает классифицированные столбцы) в качестве параметров:

```
#ifdef _WIN32
#include <windows.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include <msodbcsql.h>
#include <stdio.h>
SQLHANDLE env, dbc, stmt;
void checkRC_exit(SQLRETURN rc, SQLHANDLE hand, SQLSMALLINT htype, int retcode, char *action)
{
    if ((rc == SQL_ERROR || rc == SQL_SUCCESS_WITH_INFO) && hand)
    {
        char msg[1024], state[6];
        int i = 0;
        SQLRETURN rc2;
        SQLINTEGER err;
        SQLSMALLINT lenout;
        while ((rc2 = SQLGetDiagRec(htype, hand, ++i, state, &err, msg, sizeof(msg), &lenout)) == SQL_SUCCESS ||
            rc2 == SQL_SUCCESS_WITH_INFO)
            printf("%d (%d)[%s]%s\n", i, err, state, msg);
    }
    if (rc == SQL_ERROR && retcode)
    {
        printf("Error occurred%s%s\n", action ? " upon " : "", action ? action : "");
        exit(retcode);
    }
}
void printLabelInfo(char *type, char **pptr)
{
    char *ptr = *pptr;
    unsigned short nlabels;
    printf("----- %s(%u) -----\n", type, nlabels = *(unsigned short*)ptr);
    ptr += sizeof(unsigned short);
    while (nlabels--)
    {
        int namelen, idlen;
        char *nameptr, *idptr;
        namelen = *ptr++;
        nameptr = ptr;
        ptr += namelen * 2;
        idlen = *ptr++;
        idptr = ptr;
        ptr += idlen * 2;
        wprintf(L"Name: \"%.*s\" Id: \"%.*s\"\n", namelen, nameptr, idlen, idptr);
    }
    *pptr = ptr;
}
int main(int argc, char **argv)
{
    unsigned char *dcbuf;
    unsigned int dclen = 0;
    SQLRETURN rc;
    SQLHANDLE ird;
    if (argc < 3)
    {
        fprintf(stderr, "usage: dataclassification connstr query\n");
        return 1;
    }
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_ENV, 0, &env), 0, 0,
        2, "allocate environment");
    checkRC_exit(SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0), env, SQL_HANDLE_ENV,
        3, "set ODBC version");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc), env, SQL_HANDLE_ENV,
        4, "allocate connection");
    checkRC_exit(SQLDriverConnect(dbc, 0, argv[1], SQL_NTS, 0, 0, 0, SQL_DRIVER_NOPROMPT), dbc, SQL_HANDLE_DBC,
        5, "connect to server");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt), dbc, SQL_HANDLE_DBC,
        6, "allocate statement");
    checkRC_exit(SQLExecDirect(stmt, argv[2], SQL_NTS), stmt, SQL_HANDLE_STMT,
        7, "execute query");
    checkRC_exit(SQLGetStmtAttr(stmt, SQL_ATTR_IMP_ROW_DESC, (SQLPOINTER)&ird, SQL_IS_POINTER, 0), stmt, SQL_HANDLE_STMT,
        8, "get IRD handle");
    rc = SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, 0, &dclen);
    if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
    {
        checkRC_exit(rc, ird, SQL_HANDLE_DESC, 0, 0);
        printf("Error reading SQL_CA_SS_DATA_CLASSIFICATION IRD field. Ensure that the driver and\n"
            "server both support the Data Classification feature, and that the query returns columns\n"
            "with classification information.\n");
    }
    else
    {
        SQLINTEGER dclenout;
        unsigned char *dcptr;
        unsigned short ncols;
        printf("Data Classification information (%u bytes):\n", dclen);
        if (!(dcbuf = malloc(dclen)))
        {
            printf("Memory Allocation Error");
            return 9;
        }
        checkRC_exit(SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, dclen, &dclenout),
            ird, SQL_HANDLE_DESC, 10, "reading SQL_CA_SS_DATA_CLASSIFICATION");
        dcptr = dcbuf;
        printLabelInfo("Labels", &dcptr);
        printLabelInfo("Information Types", &dcptr);
        printf("----- Column Sensitivities(%u) -----\n", ncols = *(unsigned short*)dcptr);
        dcptr += sizeof(unsigned short);
        while (ncols--)
        {
            unsigned short nprops = *(unsigned short*)dcptr;
            dcptr += sizeof(unsigned short);
            while (nprops--)
            {
                unsigned short labelidx, typeidx;
                labelidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                typeidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                printf(labelidx == 0xFFFF ? "(none) " : "%u ", labelidx);
                printf(typeidx == 0xFFFF ? "(none)\n" : "%u\n", typeidx);
            }
            printf("-----\n");
        }
        if (dcptr != dcbuf + dclen)
        {
            printf("Error: unexpected parse of DATACLASSIFICATION data\n");
            return 11;
        }
        free(dcbuf);
    }
    return 0;
}
```

## <a name="bkmk-version"></a>Поддерживаемая версия
Microsoft ODBC Driver 17,2 позволяет получить сведения о классификации данных с помощью `SQLGetDescField`, если `FieldIdentifier` имеет значение `SQL_CA_SS_DATA_CLASSIFICATION` (1237). 

Начиная с Microsoft ODBC Driver 17.4.1.1 можно извлечь версию классификации данных, поддерживаемую сервером, с помощью `SQLGetDescField`, используя идентификатор поля `SQL_CA_SS_DATA_CLASSIFICATION_VERSION` (1238). В 17.4.1.1 для поддерживаемой версии классификации данных задано значение "2".

 

Начиная с 17.4.2.1 была введена версия по умолчанию для классификации данных, для которой задано значение "1", а драйвер версии сообщает о том, что SQL Server поддерживается. Новый атрибут подключения `SQL_COPT_SS_DATACLASSIFICATION_VERSION` (1400) позволяет приложению изменять поддерживаемую версию классификации данных с "1" до максимальной поддерживаемой версии.  

Пример 

Чтобы задать версию, этот вызов должен быть сделан прямо перед вызовом SQLConnect или SQLDriverConnect:
```
ret = SQLSetConnectAttr(dbc, SQL_COPT_SS_DATACLASSIFICATION_VERSION, (SQLPOINTER)2, SQL_IS_INTEGER);
```

Значение поддерживаемой в настоящее время версии классификации данных можно ретирвед через вызов SQLGetConnectAttr: 
```
ret = SQLGetConnectAttr(dbc, SQL_COPT_SS_DATACLASSIFICATION_VERSION, (SQLPOINTER)&dataClassVersion, SQL_IS_INTEGER, 0);
```

