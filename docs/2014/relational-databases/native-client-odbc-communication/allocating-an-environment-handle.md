---
title: Выделение дескриптора среды | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dea32df21f36220959a5c3ed49a7a927b59797ce
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425943"
---
# <a name="allocating-an-environment-handle"></a>Выделение дескриптора среды
  Прежде чем в приложении появится возможность вызвать какую-либо функцию ODBC, необходимо инициализировать среду ODBC и выделить дескриптор среды. Это — глобальный дескриптор контекста и заполнитель для других дескрипторов в ODBC. Это делается путем вызова **SQLAllocHandle** с *HandleType* параметр значение SQL_HANDLE_ENV и *InputHandle* установленным в значение SQL_NULL_HANDLE.  
  
 После выделения дескриптора среды приложение должно установить атрибуты среды, чтобы указать, какая версия вызовов функций ODBC будет использоваться. Для использования ODBC 3. *x* вызов функции, [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) с *атрибут* параметр значение SQL_ATTR_ODBC_VERSION и *ValuePtr* присвоено SQL_OV_ ODBC3.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
