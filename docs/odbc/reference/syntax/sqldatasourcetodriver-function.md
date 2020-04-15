---
title: Функция S'LDataSourceToDriver Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92df58b76a9a11d0d4ab9821756bff014ecae29a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301194"
---
# <a name="sqldatasourcetodriver-function"></a>Функция SQLDataSourceToDriver
**SLDataSourceToDriver** поддерживает переводы для драйверов ODBC. Эта функция не называется приложениями с поддержкой ODBC; приложения запрашивают перевод через **S'LsetConnectAttr**. Драйвер, связанный с *соединением,* указанным в **S'LSetConnectAttr,** вызывает указанный DLL для выполнения переводов всех данных, перетекающих из источника данных в драйвер. DLL перевода по умолчанию может быть указан в файле инициализации ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
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
 (Вход) Значение опциона.  
  
 *fSqlType*  
 (Вход) Тип данных S'L. Этот аргумент говорит водителю, как преобразовать *rgbValueIn* в форму, приемлемую для приложения. Список действительных типов данных S'L можно узнать в разделе [«Типы данных»](../../../odbc/reference/appendixes/sql-data-types.md) в приложении D: Типы данных.  
  
 *rgbValueIn*  
 (Вход) Значение для перевода.  
  
 *cbValueIn*  
 (Вход) Длина *rgbValueIn*.  
  
 *rgbValueOut*  
 (Выход) Результат перевода.  
  
> [!NOTE]  
>  Перевод DLL не сводит на нет это значение.  
  
 *cbValueOutMax*  
 (Вход) Длина *rgbValueOut*.  
  
 *pcbValueOut*  
 (Выход) Общее количество байтов (за исключением байт-нанули) доступно для возврата в *rgbValueOut.*  
  
 Для символов или двоичных данных, если это больше или равно *cbValueOutMax*, данные в *rgbValueOut* усечены до *cbValueOutMax* байтов.  
  
 Для всех других типов данных значение *cbValueOutMax* игнорируется, а перевод DLL предполагает, что размер *rgbValueOut* является размером типа данных C по умолчанию типа данных, указанного *с fSqlType.*  
  
 Аргумент *pcbValueOut* может быть нулевым указателем.  
  
 *szErrorMsg*  
 (Выход) Указатель на хранение сообщения об ошибке. Это пустая строка, если перевод не сработал.  
  
 *cbErrorMsgMax*  
 (Вход) Длина *szErrorMsg*.  
  
 *pcbErrorMsg*  
 (Выход) Указатель на общее количество байтов (за исключением байт-на-аруле) можно вернуть в *szErrorMsg.* Если это больше или равно *cbErrorMsg*, данные в *szErrorMsg* усечендо до *cbErrorMsgMax* минус нулевой прекращения характер. *PCbErrorMsg* аргумент может быть нулевой указатель.  
  
## <a name="returns"></a>Результаты  
 ПРАВДА, если перевод был успешным, FALSE, если перевод не удалось.  
  
## <a name="comments"></a>Комментарии  
 Водитель вызывает **S'LDataSourceToDriver** для перевода всех данных (данные набора результатов, имена таблиц, количество строк, сообщения об ошибках и т.д.), передавая сьонуа от источника данных к водителю. Перевод DLL может не переводить некоторые данные, в зависимости от типа данных и цели перевода DLL; например, DLL, который переводит данные символов с одной страницы кода на другую, игнорирует все числовые и двоичные данные.  
  
 Значение *fOption* устанавливается к значению *vParam,* указанному по телефону **s'LSetConnectAttr** с SQL_ATTR_TRANSLATE_OPTION атрибутом. Это 32-битное значение, которое имеет определенное значение для данного перевода DLL. Например, он может указать определенный перевод набора символов.  
  
 Если тот же буфер указан для *rgbValueIn* и *rgbValueOut,* перевод данных в буфере будет выполнен на месте.  
  
 Хотя *cbValueIn*, *cbValueOutMax*, и *pcbValueOut* имеют тип SDWORD, **S'LDataSourceToDriver** не обязательно поддерживать огромные указатели.  
  
 Если **S'LDataSourceToDriver** вернет FALSE, усечение данных могло произойти во время перевода. Если *pcbValueOut* (количество байтов, доступных для возврата в буфере вывода) больше, чем *cbValueOutMax* (длина выходного буфера), то усечение произошло. Водитель должен определить, является ли усечение приемлемым. Если усечение не произошло, **S'LDataSourceToDriver** вернулся FALSE из-за другой ошибки. В любом случае, определенное сообщение об ошибке возвращается в *szErrorMsg*.  
  
 Для получения дополнительной информации о переводе данных, [см.](../../../odbc/reference/develop-app/translation-dlls.md)  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Перевод данных, отправляемых в источник данных|[СЗЛДрайверТоДатаИсточник](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Возвращение параметра атрибута соединения|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Установка атрибута соединения|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
