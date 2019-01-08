---
title: Функция SQLDataSourceToDriver | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSourceToDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSourceToDriver
helpviewer_keywords:
- SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0ad4a98689db00c6dcb484e7a04bb973d2e1761
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206263"
---
# <a name="sqldatasourcetodriver-function"></a>Функция SQLDataSourceToDriver
**SQLDataSourceToDriver** supportstranslations для драйверов ODBC. Эта функция не вызывается приложений с поддержкой ODBC; приложения запрашивают трансляции с помощью **SQLSetConnectAttr**. Драйвера, связанного с *ConnectionHandle* указано в **SQLSetConnectAttr** вызывает указанную библиотеку DLL для выполнения преобразования всех данных, поступающих из источника данных к драйверу. Перевод DLL по умолчанию можно указать в файле инициализации ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLDataSourceToDriver(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *fOption*  
 [Вход] Значение параметра.  
  
 *fSqlType*  
 [Вход] Тип данных SQL. Этот аргумент сообщает драйверу о том, как преобразовать *rgbValueIn* в форму, допустимые для приложения. Список допустимых типов данных SQL, см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) разделе в приложение г Типы данных.  
  
 *rgbValueIn*  
 [Вход] Преобразуемое значение.  
  
 *cbValueIn*  
 [Вход] Длина *rgbValueIn*.  
  
 *rgbValueOut*  
 [Выход] Результат преобразования.  
  
> [!NOTE]  
>  Преобразование библиотеки DLL не завершите это значение.  
  
 *cbValueOutMax*  
 [Вход] Длина *rgbValueOut*.  
  
 *pcbValueOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) для возврата в *rgbValueOut*.  
  
 Для символьных или двоичных данных, если это больше, чем или равно *cbValueOutMax*, данные в *rgbValueOut* усекается до *cbValueOutMax* байт.  
  
 Для всех других типов данных, значение *cbValueOutMax* игнорируется и библиотеки DLL перевода предполагает, что размер *rgbValueOut* — это размер типа данных C по умолчанию тип данных SQL, указанный с помощью *fSqlType*.  
  
 *PcbValueOut* аргументом может быть пустым указателем.  
  
 *szErrorMsg*  
 [Выход] Указатель на хранилище для сообщения об ошибке. Это пустая строка, если не удалось выполнить преобразование.  
  
 *cbErrorMsgMax*  
 [Вход] Длина *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Выход] Указатель на общее число байтов (за исключением байтов конечное значение null) для возврата в *szErrorMsg*. Если это больше, чем или равно *cbErrorMsg*, данные в *szErrorMsg* усекается до *cbErrorMsgMax* минус знак завершения null. *PcbErrorMsg* аргументом может быть пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Значение TRUE, если преобразование выполнено успешно, FALSE Если преобразование завершилось неудачей.  
  
## <a name="comments"></a>Комментарии  
 Драйвер вызывает **SQLDataSourceToDriver** для преобразования alldata (результирующий набор данных, имена таблиц, количество строк, сообщения об ошибках и т. д.) передача из данных источника к драйверу. Преобразование библиотеки DLL не может передать некоторых данных в зависимости от типа данных и назначение перевода DLL. например библиотеку DLL, которая преобразует символьные данные из одной кодовой страницы в другую не учитывает все числовые и двоичные данные.  
  
 Значение *fOption* присваивается значение *vParam* , задаются путем вызова **SQLSetConnectAttr** с атрибутом SQL_ATTR_TRANSLATE_OPTION. Это 32-разрядное значение, которое имеет особое значение для определенной записи преобразования DLL. Например может указать набор определенным символом перевода.  
  
 Если указан этот же буфер для *rgbValueIn* и *rgbValueOut*, преобразование данных в буфере будет выполняться на месте.  
  
 Несмотря на то что *cbValueIn*, *cbValueOutMax*, и *pcbValueOut* относятся к типу SDWORD, **SQLDataSourceToDriver** не обязательно поддерживает огромное указатели.  
  
 Если **SQLDataSourceToDriver** возвращает FALSE, усечение данных может произойти во время преобразования. Если *pcbValueOut* (количество байтов, доступных для возврата в выходном буфере) больше, чем *cbValueOutMax* (длина выходного буфера), а затем произошло усечение. Драйвер необходимо определить, было ли усечение приемлемо. Если усечение не было, **SQLDataSourceToDriver** возвращается значение FALSE из-за другой ошибки. В любом случае возвращается сообщение об ошибке в *szErrorMsg*.  
  
 Дополнительные сведения о преобразовании данных см. в разделе [библиотеки DLL преобразования](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Преобразование данных, отправляемых в источнике данных|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Возвращает значение атрибута соединения|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Присвоение атрибуту соединения|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
