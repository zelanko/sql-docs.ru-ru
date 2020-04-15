---
title: Функция S'LDriverToDataИсточник (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverToDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverToDataSource
helpviewer_keywords:
- SQLDriverToDataSource function [ODBC]
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7db7e4b20a35e047dca94cb72d8a6888fb670
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302755"
---
# <a name="sqldrivertodatasource-function"></a>Функция SQLDriverToDataSource
**S'LDriverToDataSource** поддерживает переводы для драйверов ODBC. Эта функция не называется приложениями с поддержкой ODBC; приложения запрашивают перевод через **S'LsetConnectAttr**. Драйвер, связанный с *соединением,* указанным в **S'LSetConnectAttr,** вызывает указанный DLL для выполнения переводов всех данных, перетекающих от драйвера к источнику данных. DLL перевода по умолчанию может быть указан в файле инициализации ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLDriverToDataSource(  
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
 (Вход) Тип данных ODBC S'L. Этот аргумент говорит водителю, как преобразовать *rgbValueIn* в форму, приемлемую для источника данных. Для списка действительных типов данных [SQL Data Types](../../../odbc/reference/appendixes/sql-data-types.md)S'L см.  
  
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
 Водитель вызывает **S'LDriverToDataSource** для перевода всех данных (заявления, параметры ИЗЛ и т.д.), переходящего от драйвера к источнику данных. Перевод DLL может не переводить некоторые данные, в зависимости от типа данных и цели перевода DLL. Например, DLL, который переводит данные символов с одной страницы кода на другую, игнорирует все числовые и двоичные данные.  
  
 Значение *fOption* устанавливается к значению *vParam,* указанному по телефону **s'LSetConnectAttr** с SQL_ATTR_TRANSLATE_OPTION атрибутом. Это 32-битное значение, которое имеет определенное значение для данного перевода DLL. Например, он может указать определенный перевод набора символов.  
  
 Если тот же буфер указан для *rgbValueIn* и *rgbValueOut,* перевод данных в буфере будет выполнен на месте.  
  
 Хотя *cbValueIn*, *cbValueOutMax*, и *pcbValueOut* имеют тип SDWORD, **S'LDriverToDataSource** не обязательно поддерживает огромные указатели.  
  
 Если **S'LdriverToDataSource** вернет FALSE, усечение данных могло произойти во время перевода. Если *pcbValueOut* (количество байтов, доступных для возврата в буфере вывода) больше, чем *cbValueOutMax* (длина выходного буфера), то усечение произошло. Водитель должен определить, является ли усечение приемлемым. Если усечение не произошло, **S'LDriverToDataSource** вернулся FALSE из-за другой ошибки. В любом случае, определенное сообщение об ошибке возвращается в *szErrorMsg*.  
  
 Для получения дополнительной информации о переводе данных, [см.](../../../odbc/reference/develop-app/translation-dlls.md)  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Перевод данных, возвращенных из источника данных|[СЗЛДатаИсточникТоДрайвер](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|Возвращение параметра атрибута соединения|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Установка атрибута соединения|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
