---
title: Атрибуты подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c295ce88eedf1d4cddc4173f5dea39c44b01f83d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299045"
---
# <a name="connection-attributes"></a>Атрибуты соединения
Атрибуты соединения являются характеристиками соединения. Например, поскольку транзакции выполняются на уровне соединения, уровень изоляции транзакции является атрибутом соединения. Аналогично, время ожидания входа или количество секунд ожидания при попытке подключения до истечения времени ожидания — это атрибут соединения.  
  
 Атрибуты соединения задаются с помощью **SQLSetConnectAttr** и их текущих параметров, полученных с помощью **SQLGetConnectAttr**. Если **SQLSetConnectAttr** вызывается до загрузки драйвера, диспетчер драйверов сохраняет атрибуты в своей структуре соединения и задает их в драйвере в процессе подключения. Не требуется, чтобы приложение установило какие-либо атрибуты подключения. все атрибуты соединения имеют значения по умолчанию, некоторые из которых зависят от драйвера.  
  
 Атрибут соединения можно задать до или после соединения либо в зависимости от атрибута и драйвера. Время ожидания входа (SQL_ATTR_LOGIN_TIMEOUT) применяется к процессу подключения и вступает в силу только в том случае, если установлен перед подключением. Атрибуты, указывающие, следует ли использовать библиотеку курсоров ODBC (SQL_ATTR_ODBC_CURSORS), и размер сетевого пакета (SQL_ATTR_PACKET_SIZE) должен быть установлен перед подключением, так как библиотека курсоров ODBC находится между диспетчером драйверов и драйвером и, следовательно, должна быть загружена перед драйвером.  
  
 Атрибуты, указывающие, доступен ли источник данных только для чтения или для чтения и записи (SQL_ATTR_ACCESS_MODE), а текущий каталог (SQL_ATTR_CURRENT_CATALOG) можно задать до или после подключения, в зависимости от драйвера. Однако взаимодействующие приложения устанавливают их перед подключением, так как некоторые драйверы не поддерживают их изменение после подключения.  
  
 Некоторые атрибуты соединения имеют значение по умолчанию до того, как соединение установлено, а другие — нет. Это SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE и SQL_ATTR_TRACEFILE.  
  
 Атрибуты подключения перевода (SQL_ATTR_TRANSLATE_DLL и SQL_ATTR_TRANSLATE_OPTION) должны быть установлены после соединения.  
  
 Все остальные атрибуты соединения можно задать в любое время. Дополнительные сведения см. в описании функции [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) . (Атрибуты соединения не могут быть установлены на уровне среды путем вызова **SQLSetEnvAttr**.)
