---
title: Картирование типов данных (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92426c854758d07a9d62ec57510d202b870dd9f2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304637"
---
# <a name="mapping-data-types-odbc"></a>Сопоставление типов данных (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC отображает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных с S'L к типам данных ODBC S-L. В последующих разделах обсуждаются типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL с типами данных ODBC SQL, с которыми они сопоставляются. В разделах также обсуждаются типы данных ODBC SQL и соответствующие им типы данных ODBC C, а также поддерживаемые преобразования и преобразования по умолчанию.  
  
> [!NOTE]  
>  Карты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]типа **таймштампов** SQL_BINARY или SQL_VARBINARY типданных данных ODBC, поскольку значения в столбцах **времени** являются не значениями **времени времени,** а **бинарными (8)** или **варбинарными (8)** значениями, указывающими последовательность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] активности в строке. Если драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] встречает значение типа SQL_C_WCHAR (Юникод), что означает нечетное число байт, то последний нечетный байт усекается.  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>Работа с типом данных sql_variant в ODBC  
 Колонка **типа sql_variant** данных может содержать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любой из типов данных, за исключением крупных объектов (LOBs), таких как **текст,** **ntext**и **изображение.** Например, столбец может содержать **небольшие** значения для некоторых строк, значения **поплавка** для других строк и значения **char/nchar** в оставшейся части.  
  
 Тип **данных sql_variant** похож на тип данных **Variant** в Microsoft Visual Basic®.  
  
### <a name="retrieving-data-from-the-server"></a>Получение данных с сервера  
 ODBC не имеет понятия типов вариантов, ограничивающих использование **типа данных** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sql_variant с драйвером ODBC в . В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]случае удевания связывания **sql_variant** тип данных должен быть привязан к одному из задокументированных типов данных ODBC. **SQL_CA_SS_VARIANT_TYPE**, новый атрибут, специфичный для драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC, возвращает пользователю тип экземпляра в **sql_variant** столбец.  
  
 Если привязка не указана, функция [S'LGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) может быть использована для определения типа данных экземпляра в **sql_variant** столбеце.  
  
 Для получения **sql_variant** данных выполните эти действия.  
  
1.  Позвоните **в S'LFetch,** чтобы позиционировать исправленную строку.  
  
2.  Позвоните в **S'LGetData,** указав SQL_C_BINARY для типа и 0 для длины данных. Это заставляет водителя читать **sql_variant** заголовок. Заголовок предоставляет тип данных этого экземпляра в **sql_variant** столбце. **S'LGetData** возвращает размер (в байтах) значения.  
  
3.  Позвоните [в S'LColAttribute,](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) указав **SQL_CA_SS_VARIANT_TYPE** в качестве значения атрибута. Эта функция вернет тип данных C экземпляра в **sql_variant** столбец клиенту.  
  
 Фрагмент кода, демонстрирующий вышеуказанные шаги:  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Если пользователь создает привязку с помощью [S'LBindCol,](../../relational-databases/native-client-odbc-api/sqlbindcol.md)водитель считывает метаданные и данные. Затем драйвер преобразует данные к соответствующему типу ODBC, указанному в привязке.  
  
### <a name="sending-data-to-the-server"></a>Отправка данных на сервер  
 **SQL_SS_VARIANT,** новый тип данных, специфичный для драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Native Client, используется для данных, отправляемых в **sql_variant** столбец. При отправке данных на сервер с использованием параметров (например, INSERT INTO TableName VALUES (?,?)) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указания информации о параметрах, включая тип C и соответствующий тип, используется [система s'LBindParameter.](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC преобразует тип данных C в один из соответствующих **sql_variant** подтипов.  
  
## <a name="see-also"></a>См. также:  
 [Результаты обработки &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
