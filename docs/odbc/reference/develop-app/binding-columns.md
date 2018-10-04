---
title: Привязка столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 035e525116622a3c55e50547958b86fc2ee9bdb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678362"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных возвращается в приложение в переменных, которые приложение, выделенной для этой цели. Прежде чем это можно сделать, необходимо связать приложение, или *привязать*, эти переменные к столбцам результирующего набора; по сути, этот процесс — так же, как привязка переменных приложения для параметров инструкции. Если приложение связывает переменную, чтобы столбец результирующего набора, он описывает эту переменную, адрес, тип данных и т. д. — к драйверу. Драйвер сохраняет эту информацию в структуре, он поддерживает для этой инструкции и использует сведения для возврата значения из столбца при выборке строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
