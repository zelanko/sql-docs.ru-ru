---
title: Функция S'LsetConnectattrFordbinfo Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f43a0fc6cd02fe566579a543667f9a4c4c1a108
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301891"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>Функция SQLSetConnectAttrForDbcInfo
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **СЗЛСЕТКоннЕКТтрНадДЦбИнфо** такой же, как **и s'LSetConnectAttr,** но он устанавливает атрибут на токене информации о подключении, а не на ручке соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbcInfoToken*  
 (Вход) Ручка маркера.  
  
 *Атрибут*  
 (Вход) Атрибут для установки. Список действительных атрибутов специфичен для драйвера и такой же, как и для [S'LSetConnectAttr.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
 *ValuePtr*  
 (Вход) Указатель на значение, связанное с *атрибутом.* В зависимости от значения *Attribute,* *ValuePtr* будет 32-битным неподписанным значением бесстыждения или укажет на нулевую строку символов. Обратите внимание, что если аргумент *Attribute* является значением для конкретного драйвера, значение в *ValuePtr* может быть подписано рядом.  
  
 *Струнная длина*  
 (Вход) Если *Attribute* является атрибутом, определяемым ODBC, и *ValuePtr* указывает на строку символов или бинарный буфер, этот аргумент должен быть длиной*в значение ValuePtr.* Для данных строки символов этот аргумент должен содержать количество байтов в строке.  
  
 Если *Attribute* является атрибутом, определяемым ODBC, а *ValuePtr* — неопределенным, *StringLength* игнорируется.  
  
 Если *атрибут* является атрибутом, определяемым драйвером, приложение указывает характер атрибута менеджеру драйвера, установив аргумент *StringLength.* *StringLength* может иметь следующие значения:  
  
-   Если *ValuePtr* является указателем на строку персонажа, то *StringLength* — это длина строки или SQL_NTS.  
  
-   Если *ValuePtr* является указателем на двоичный буфер, то приложение помещает результат SQL_LEN_BINARY_ATTR *(длина)* макроса в *StringLength.* Это ставит отрицательное значение в *StringLength*.  
  
-   Если *ValuePtr* является указателем на значение, кроме строки символов или двоичной строки, то *StringLength* должен иметь значение SQL_IS_POINTER.  
  
-   Если *ValuePtr* содержит значение с фиксированной длиной, то *StringLength* является либо SQL_IS_INTEGER, либо SQL_IS_UINTEGER, в случае необходимости.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Так же, как [и s'LSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), за исключением того, что менеджер драйвера будет использовать **HandleType** SQL_HANDLE_DBC_INFO_TOKEN и **ручку** *hDbcInfoToken*.  
  
## <a name="remarks"></a>Remarks  
 **СЗЛСЕТКоннЕКТтрНадДБИнфо** такой же, как **и s'LSetConnectAttr,** но он устанавливает атрибут на маркере информации о подключении, а не на ручке соединения. Например, если **S'LSetConnectAttr** не распознает атрибут, **S'LSetConnectAttrForDbcInfo** также должен вернуть SQL_ERROR для этого атрибута.  
  
 Всякий раз, когда водитель возвращает SQL_ERROR или SQL_INVALID_HANDLE, водитель должен игнорировать этот атрибут для вычисления идентификатора пула. Кроме того, менеджер драйвера получит диагностическую информацию от *hDbcInfoToken,* а также вернет SQL_SUCCESS_WITH_INFO в приложение в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md) Таким образом, приложение может получить подробную информацию о том, почему некоторые атрибуты не могут быть установлены.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
