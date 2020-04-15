---
title: Картирование S'LSetConnectOption (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 757b50c7e18133e02b4cf6addaa327b2053f5439
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287474"
---
# <a name="sqlsetconnectoption-mapping"></a>Сопоставление SQLSetConnectOption
Когда ODBC 2. *x* приложение вызывает **S'LSetConnectOption** через драйвер ODBC 3 *.x,* вызов  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 приведет следующим образом:  
  
-   Если *fOption* указывает на атрибут соединения, определяемый ODBC, который требует строки, менеджер драйвера вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает на атрибут соединения, определяемый ODBC, который возвращает 32-битное значение, менеджер драйвера вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибут соединения, определяемый драйвером, менеджер драйвера вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 В предыдущих трех случаях аргумент *ConnectionHandle* устанавливается на значение в *HDbc,* аргумент *Attribute* установлен на значение в *fOption,* а аргумент *ValuePtr* устанавливается на то же значение, что и *vParam.*  
  
 Поскольку менеджер драйвера не знает, нуждается ли атрибут соединения, определяемый драйвером, строкой или 32-битным значением, он должен пройти в допустимом значении для аргумента *BufferLength* **s'LSetConnectAttr.** Если драйвер определил специальную семантику для атрибутов подключения, определяемого драйвером, и его необходимо вызывать с помощью **S'LSetConnectOption,** он должен поддерживать **S'LSetConnectOption.**  
  
 Если ODBC 2. *приложение x* вызывает **s'LSetConnectOption** для установки опции оператора для драйвера ODBC 3 *.x,* и параметр был определен в ODBC 2. *x* версия драйвера, новая константа манифеста должна быть определена для опции в драйвере ODBC 3 *.x.* Если старая константа манифеста используется при вызове в **S'LSetConnectOption,** менеджер драйвера вызовет **S'LSetConnectAttr** с аргументом **StringLength,** установленным на 0.  
  
 Для драйвера ODBC 3 *.x* менеджер драйвера больше не проверяет, находится ли *fOption* между SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX, или больше, чем SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Настройка параметров оператора на уровне подключения  
 В ODBC 2. *x,* приложение может вызвать **S'LSetConnectOption,** чтобы установить опцию оператора. Когда это делается, драйвер устанавливает опцию оператора как по умолчанию для любых инструкций, позже выделенных для этого соединения. Определяется ли драйвер, устанавливает ли драйвер опцию оператора для любых существующих инструкций, связанных с указанным соединением.  
  
 Эта способность была унижается в ODBC 3 *.x*. OdBC 3 *.x* драйверам нужна только поддержка установки ODBC 2. *x* атрибуты оператора на уровне соединения, если они хотят работать с ODBC 2. *x* приложения, которые делают это. Приложения ODBC 3 *.x* никогда не должны устанавливать атрибуты оператора на уровне соединения. Атрибуты оператора ODBC 3 *.x* не могут быть установлены на уровне соединения, за исключением SQL_ATTR_METADATA_ID и SQL_ATTR_ASYNC_ENABLE атрибутов, которые являются атрибутами соединения и атрибутами оператора, и могут быть установлены на уровне соединения или уровне оператора.
