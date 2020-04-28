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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47f16160c05d1c410e3889f0bb857befe88df5b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299174"
---
# <a name="checking-feature-support-and-variability"></a>Проверка поддержки и изменчивости функций
Чтобы проверить поддержку и вариативность функций, приложения обычно вызывают **SQLGetInfo**, **SQLGetFunctions**и **SQLGetTypeInfo**. Хорошим началом является API драйвера и уровни соответствия грамматики SQL. Они содержат описание широкого уровня поддержки функций. После этого приложение может вызвать **SQLGetInfo** с другими параметрами, чтобы определить поддержку или вариативность необходимых функций, **SQLGetFunctions** , чтобы определить, поддерживаются ли функции, которые ей требуются, помимо возвращаемого уровня соответствия, а **SQLGetTypeInfo** определить, какие типы данных SQL поддерживаются.  
  
 Приложение может определить, поддерживается ли оператор или атрибут соединения путем вызова **SQLSetStmtAttr** или **SQLSetConnectAttr** с этим атрибутом. Если функция возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, атрибут поддерживается; Если он возвращает SQL_ERROR и SQLSTATE HYC00 (необязательный компонент не реализован), атрибут не поддерживается.  
  
 Приложения также могут определить ограниченный объем информации перед подключением к драйверу, вызвав **SQLDrivers**.
