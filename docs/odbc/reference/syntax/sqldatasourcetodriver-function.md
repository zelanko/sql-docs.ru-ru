---
title: Функция SQLDataSourceToDriver | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bcdad2099be94a719333d4e0754318f7c00572df
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 [Вход] Тип данных SQL. Этот аргумент сообщает драйверу о том, как преобразовать *rgbValueIn* в форму, допустимые для приложения. Список допустимых типов данных SQL см. в разделе [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) раздел в типах данных приложение D:.  
  
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
  
 Для символьных или двоичных данных, если это больше или равно *cbValueOutMax*, данные в *rgbValueOut* усекается до *cbValueOutMax* байт.  
  
 Для всех других типов данных, значение *cbValueOutMax* игнорируется и перевод DLL предполагает, что размер *rgbValueOut* — это размер типа данных C по умолчанию типа данных SQL, указанного с *fSqlType*.  
  
 *PcbValueOut* аргумент может быть пустой указатель.  
  
 *szErrorMsg*  
 [Выход] Указатель хранилища для сообщение об ошибке. Это пустая строка, если произошел сбой преобразования.  
  
 *cbErrorMsgMax*  
 [Вход] Длина *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Выход] Указатель на общее количество байтов (за исключением байтов конечное значение null) для возврата в *szErrorMsg*. Если это больше или равно *cbErrorMsg*, данные в *szErrorMsg* усекается до *cbErrorMsgMax* конечное значение null знак «минус». *PcbErrorMsg* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Значение TRUE, если преобразование успешно выполнен, FALSE, если произошел сбой преобразования.  
  
## <a name="comments"></a>Комментарии  
 Драйвер вызывает **SQLDataSourceToDriver** для перевода alldata (результирующий набор данных, имена таблиц, количество строк, сообщения об ошибках и т. д.) передача из данных источника к драйверу. Преобразование библиотеки DLL не может переводить некоторые данные, в зависимости от типа данных и назначение сдвига DLL. например библиотеки DLL, которая преобразует символьные данные из одной кодовой страницы в другую не учитывает все числовые и двоичные данные.  
  
 Значение *fOption* присвоено значение *vParam* задаются путем вызова **SQLSetConnectAttr** с атрибутом SQL_ATTR_TRANSLATE_OPTION. Это 32-разрядное значение, которое имеет особое значение для заданного перевода DLL. Например он может укажите определенных перевод кодировки.  
  
 Если для того же буфера *rgbValueIn* и *rgbValueOut*, выполняется преобразование данных в буфере на месте.  
  
 Несмотря на то что *cbValueIn*, *cbValueOutMax*, и *pcbValueOut* относятся к типу SDWORD, **SQLDataSourceToDriver** не обязательно поддерживает огромное указатели.  
  
 Если **SQLDataSourceToDriver** возвращает FALSE, усечение данных может произойти во время преобразования. Если *pcbValueOut* (число байтов, доступных для возврата в выходном буфере) больше, чем *cbValueOutMax* (длина выходного буфера), а затем произошло усечение. Драйвер должен определить, успешно ли усечение приемлемым. Если усечение не проводилась, **SQLDataSourceToDriver** вернул значение FALSE из-за другой ошибки. В любом случае будет возвращено сообщение об ошибке в *szErrorMsg*.  
  
 Дополнительные сведения о преобразовании данных см. в разделе [DLL перевода](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Преобразования данных, отправляемых в источнике данных|[Трансляции SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Возврат значения атрибута соединения|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Присвоение атрибуту соединения|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
