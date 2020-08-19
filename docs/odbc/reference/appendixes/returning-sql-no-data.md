---
description: Возврат SQL_NO_DATA
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24efdd88d16ba31a2b70dfb75ad21adee08c6f1c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424976"
---
# <a name="returning-sql_no_data"></a>Возврат SQL_NO_DATA
Когда приложение ODBC *2. x* ВОРКИНГВИС драйвер ODBC *3. x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData**и выполнялась инструкция UPDATE или DELETE с поиском, но не влияет на строки в источнике данных, драйвер ODBC *3. x* должен возвращать SQL_SUCCESS. Когда приложение ODBC *3. x* , работающее с драйвером ODBC *3. x* , вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** с тем же результатом, драйвер ODBC *3. x* должен возвращать SQL_NO_DATA.  
  
 Если искомая инструкция UPDATE или DELETE в пакете инструкций не влияет на строки в источнике данных, **SQLMoreResults** возвращает SQL_SUCCESS. Он не может возвращать SQL_NO_DATA, так как это означает, что больше нет результатов, а не из-за искомого обновления или удаления, которое не затронуло ни одной строки.
