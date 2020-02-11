---
title: Проверка поддержки функций и вариативность | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062666"
---
# <a name="checking-feature-support-and-variability"></a>Проверка поддержки и изменчивости функций
Чтобы проверить поддержку и вариативность функций, приложения обычно вызывают **SQLGetInfo**, **SQLGetFunctions**и **SQLGetTypeInfo**. Хорошим началом является API драйвера и уровни соответствия грамматики SQL. Они содержат описание широкого уровня поддержки функций. После этого приложение может вызвать **SQLGetInfo** с другими параметрами, чтобы определить поддержку или вариативность необходимых функций, **SQLGetFunctions** , чтобы определить, поддерживаются ли функции, которые ей требуются, помимо возвращаемого уровня соответствия, а **SQLGetTypeInfo** определить, какие типы данных SQL поддерживаются.  
  
 Приложение может определить, поддерживается ли оператор или атрибут соединения путем вызова **SQLSetStmtAttr** или **SQLSetConnectAttr** с этим атрибутом. Если функция возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, атрибут поддерживается; Если он возвращает SQL_ERROR и SQLSTATE HYC00 (необязательный компонент не реализован), атрибут не поддерживается.  
  
 Приложения также могут определить ограниченный объем информации перед подключением к драйверу, вызвав **SQLDrivers**.
