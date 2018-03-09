---
title: "Роль драйвера | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7381b239b87d4979545504e01f552a9be21fd694
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="role-of-the-driver"></a>Роль драйвера
Драйвер проверяет все ошибки и предупреждения, не проверяется диспетчером драйверов и упорядочивает записи состояния, которые он приводит к возникновению ошибки. (ODBC 2. *x* драйвер не упорядочивает записи состояния.) Сюда относятся ошибки и предупреждения в усечение данных, преобразования данных, синтаксис и некоторые переходы между состояниями. Драйвер также может проверять ошибки и предупреждения, частично проверяется диспетчером драйверов. Например несмотря на то, что диспетчер драйверов проверяет ли значение *операции* в **SQLSetPos** допустим, драйвер должен проверить, поддерживается ли.  
  
 Драйвер также сопоставляет *собственные ошибки* — то есть ошибки, возвращаемых источником данных, чтобы SQLSTATE. Например драйвер может сопоставить ряд различных собственные ошибки недопустимый синтаксис SQL для SQLSTATE 42000 (синтаксическая ошибка или нарушение доступа). Драйвер возвращает номер собственной ошибки в поле SQL_DIAG_NATIVE записи состояния. Документация по драйверу должно отображаться как ошибки и предупреждения сопоставляются из источника данных аргументов в **SQLGetDiagRec** и **SQLGetDiagField**.
