---
title: Проверка поддержки и изменчивости функций | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 21495e538a554a477336d1a92926c11fe762c5af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062666"
---
# <a name="checking-feature-support-and-variability"></a>Проверка поддержки и изменчивости функций
Чтобы проверить, поддержки и изменчивости функций, приложения обычно вызывают **SQLGetInfo**, **SQLGetFunctions**, и **SQLGetTypeInfo**. Хорошей отправной точкой является драйвера API и SQL грамматики уровни соответствия. Они описывают широкий уровней поддержки. Затем приложение может вызвать **SQLGetInfo** с другими параметрами для определения поддержки или изменчивость компоненты, необходимые, **SQLGetFunctions** для определения ли функции его потребностей за пределы возвращенного уровень соответствия, поддерживаются, и **SQLGetTypeInfo** для определения, какие типы данных SQL поддерживаются.  
  
 Приложение может определить, поддерживается ли атрибут инструкции или соединения, вызвав **SQLSetStmtAttr** или **SQLSetConnectAttr** с этим атрибутом. Если функция возвращает значение SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, атрибут поддерживается; Если возвращается значение SQL_ERROR и SQLSTATE HYC00 (дополнительная возможность, не реализована), атрибут не поддерживается.  
  
 Приложения также могут определять, ограниченный объем сведений перед подключением к драйверу, вызвав **SQLDrivers**.
