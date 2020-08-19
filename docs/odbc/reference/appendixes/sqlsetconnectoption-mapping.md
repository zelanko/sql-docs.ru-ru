---
description: Сопоставление SQLSetConnectOption
title: Сопоставление SQLSetConnectOption | Документация Майкрософт
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
ms.openlocfilehash: 6c1f1379bfd2bbc2faccf719d68009ed63b350fd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476966"
---
# <a name="sqlsetconnectoption-mapping"></a>Сопоставление SQLSetConnectOption
При использовании ODBC 2. Приложение *x* вызывает **SQLSETCONNECTOPTION** через драйвер ODBC 3 *. x* , вызов  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 результат будет следующим:  
  
-   Если *параметром fOption* указывает определенный ODBC атрибут соединения, для которого требуется строка, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *параметром fOption* указывает определенный ODBC атрибут соединения, возвращающий 32-разрядное целое значение, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Если *параметром fOption* указывает на определенный драйвером атрибут соединения, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 В предыдущих трех случаях аргументу *коннектионхандле* присваивается значение в *хдбк*, аргументу *атрибута* присваивается значение в *параметром fOption*, а аргументу *ValuePtr* присваивается то же значение, что и *впарам*.  
  
 Так как диспетчер драйверов не знает, что для атрибута соединения, определяемого драйвером, требуется строка или 32-разрядное целое число, ему необходимо передать допустимое значение *BufferLength* аргумента BufferLength **SQLSetConnectAttr**. Если драйвер определил специальную семантику для атрибутов подключения, определенных драйвером, и должен вызываться с помощью **SQLSetConnectOption**, он должен поддерживать **SQLSetConnectOption**.  
  
 Если ODBC 2. Приложение *x* вызывает **SQLSetConnectOption** , чтобы установить параметр инструкции для конкретного драйвера в драйвере ODBC 3 *. x* , а параметр был определен в ODBC 2. *x* версия драйвера, для параметра в драйвере ODBC 3 *. x* должна быть определена новая константа манифеста. Если в вызове **SQLSetConnectOption**используется старая константа манифеста, диспетчер драйверов выдаст **SQLSetConnectAttr** с аргументом **StringLength** , для которого установлено значение 0.  
  
 Для драйвера ODBC 3 *. x* диспетчер драйверов больше не проверяет, находится ли *параметром fOption* между SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX или больше, чем SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Установка параметров инструкции на уровне соединения  
 В ODBC 2. *x*, приложение может вызвать **SQLSetConnectOption** для задания параметра инструкции. Когда это будет сделано, драйвер устанавливает параметр инструкции по умолчанию для всех инструкций, которые позже выделяются для этого соединения. Драйвер определяет, задает ли драйвер параметр инструкции для всех существующих инструкций, связанных с указанным соединением.  
  
 Эта возможность является устаревшей в ODBC 3 *. x*. Драйверам ODBC 3 *. x* требуется только поддержка ODBC 2. атрибуты инструкции *x* на уровне соединения, если они хотят работать с ODBC 2. приложения *x* , которые это делают. Приложения ODBC 3 *. x* никогда не должны задавать атрибуты инструкций на уровне соединения. Атрибуты инструкций ODBC 3 *. x* не могут быть установлены на уровне соединения, за исключением атрибутов SQL_ATTR_METADATA_ID и SQL_ATTR_ASYNC_ENABLE, которые являются атрибутами соединения и атрибутами инструкции, и могут быть заданы на уровне соединения или инструкции.
