---
title: Атрибуты соединения | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 09b29277d74383abff1510ca7394aecad036fc7e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036438"
---
# <a name="connection-attributes"></a>Атрибуты соединения
Атрибуты соединения, характеристики соединения. Например, поскольку транзакции выполняются на уровне соединения, уровень изоляции транзакции является атрибутом соединения. Аналогичным образом время ожидания входа, то есть количество секунд ожидания при попытке подключения до истечения времени ожидания, является атрибутом соединения.  
  
 Атрибуты соединения устанавливаются с помощью **SQLSetConnectAttr** и их текущие настройки извлекаются с помощью **SQLGetConnectAttr**. Если **SQLSetConnectAttr** вызывается перед драйвер загружается в диспетчер драйверов хранилища атрибутов в своей структуре соединений и устанавливает их в драйвере как часть процесса соединения. Нет необходимости, что приложение задать любых атрибутов соединения; все атрибуты соединения имеют значения по умолчанию, некоторые из них специфические для драйвера.  
  
 Атрибут соединения можно задать до или после соединения, либо один из, в зависимости от атрибута и драйвер. Время ожидания входа (SQL_ATTR_LOGIN_TIMEOUT) применяется к процесс подключения и действующие только тогда, когда устанавливается перед соединением. Атрибутов, определяющих, следует ли использовать библиотеку курсоров ODBC (SQL_ATTR_ODBC_CURSORS) и размер сетевого пакета (SQL_ATTR_PACKET_SIZE) необходимо задать перед подключением, так как библиотека курсоров ODBC находится между диспетчера драйверов и драйвер и Поэтому необходимо загрузить до драйвера.  
  
 Атрибуты, чтобы указать источник данных доступен только для чтения или чтения и записи (SQL_ATTR_ACCESS_MODE) и текущего каталога (SQL_ATTR_CURRENT_CATALOG) можно задать до или после подключения, в зависимости от драйвера. Тем не менее взаимодействующие приложения установить их перед подключением потому, что некоторые драйверы не поддерживают их после подключения.  
  
 Некоторые атрибуты соединения по умолчанию получают до подключения, а другие — нет. Которые являются SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE и SQL_ATTR_TRACEFILE.  
  
 Атрибуты соединения перевода (SQL_ATTR_TRANSLATE_DLL и SQL_ATTR_TRANSLATE_OPTION) должен быть установлен после соединения.  
  
 Все другие атрибуты соединения можно задать в любое время. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) описание функции. (Атрибуты соединения нельзя установить на уровне среды с помощью вызова **SQLSetEnvAttr**.)
