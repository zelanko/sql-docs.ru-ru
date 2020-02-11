---
title: Возврат SQL_NO_DATA | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2613593d9c2e20d5dfa01c0a0b4f9886dbc8e889
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057132"
---
# <a name="returning-sql_no_data"></a>Возврат SQL_NO_DATA
Когда приложение ODBC *2. x* ВОРКИНГВИС драйвер ODBC *3. x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData**и выполнялась инструкция UPDATE или DELETE с поиском, но не влияет на строки в источнике данных, драйвер ODBC *3. x* должен возвращать SQL_SUCCESS. Когда приложение ODBC *3. x* , работающее с драйвером ODBC *3. x* , вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** с тем же результатом, драйвер ODBC *3. x* должен возвращать SQL_NO_DATA.  
  
 Если искомая инструкция UPDATE или DELETE в пакете инструкций не влияет на строки в источнике данных, **SQLMoreResults** возвращает SQL_SUCCESS. Он не может возвращать SQL_NO_DATA, так как это означает, что больше нет результатов, а не из-за искомого обновления или удаления, которое не затронуло ни одной строки.
