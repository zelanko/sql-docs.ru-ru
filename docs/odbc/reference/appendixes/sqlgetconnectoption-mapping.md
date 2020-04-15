---
title: Картирование S'LGetConnectOption (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d2905bd6793d032e485183c8f553cef2cdefda3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302005"
---
# <a name="sqlgetconnectoption-mapping"></a>Сопоставление SQLGetConnectOption
Когда приложение вызывает **S'LGetConnectOption** через драйвер ODBC *3.x,*  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 отображается следующим образом:  
  
-   Если *fOption* указывает на опцию подключения, определяемую ODBC, которая возвращает строку, менеджер драйвера вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает на опцию подключения, определяемую ODBC, которая возвращает 32-битное значение, менеджер драйвера вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает на опцию оператора, определяемую драйвером, менеджер драйвера вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В предыдущих трех случаях аргумент *ConnectionHandle* устанавливается на значение в *HDbc,* аргумент *Attribute* установлен на значение в *fOption,* а аргумент *ValuePtr* устанавливается на то же значение, что и *pvParam.*  
  
 Для параметров подключения строк, определяемых ODBC, менеджер драйвера устанавливает аргумент *BufferLength* в вызове к **S'LGetConnectAttr** на заданную максимальную длину (SQL_MAX_OPTION_STRING_LENGTH); для опции неструнного *соединения, BufferLength* установлен на 0.  
  
 Для драйвера ODBC *3.x* менеджер драйвера больше не проверяет, находится ли *опцион* между SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX, или больше, чем SQL_CONNECT_OPT_DRVR_START. Водитель должен проверить достоверность значений опциона.
