---
title: Запись заголовка | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: becebb5a48c06ae16c00fb72e9db5474f876dcf1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="header-record"></a>Запись заголовка
Поля в заголовочной записи содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и тип выполняемой инструкции. Заголовочная запись создается всегда, если функция возвращает SQL_INVALID_HANDLE. Полный список полей в заголовочной записи см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.
