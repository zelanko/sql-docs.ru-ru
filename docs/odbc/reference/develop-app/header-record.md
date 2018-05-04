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
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 068f48ea6a1f48242f1709e395e6e35e72f4c93f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="header-record"></a>Запись заголовка
Поля в заголовочной записи содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и тип выполняемой инструкции. Заголовочная запись создается всегда, если функция возвращает SQL_INVALID_HANDLE. Полный список полей в заголовочной записи см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.
