---
title: Сообщения об ошибке самолета ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8fa6e672b69c7791e66dc3919e6fcd22b7c3de7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293114"
---
# <a name="odbc-jet-error-messages"></a>Сообщения об ошибках ODBC Jet
Для ошибок, возникающих в источнике данных, драйвер ODBC возвращает сообщение об ошибке, возвращенное ему библиотекой файлов ODBC. Для ошибок, которые возникают в драйвере ODBC или менеджере драйвера, водитель возвращает сообщение об ошибке на основе текста, связанного с S'Lstate.  
  
 Сообщения об ошибках имеют следующий формат:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Префиксы в скобках идентифицируют местоположение ошибки. При возникновении ошибки в менеджере драйвера *источник данных* не приводится. При возникновении ошибки в исходном коде данных префиксы*поставщика*и*ODBC-компонента*идентифицируют поставщика и название компонента ODBC, получивших ошибку из источника данных.  
  
 В следующей таблице показаны сообщения об ошибках, возвращенные менеджером драйвера и драйвером ISAM:  
  
|Сообщение об ошибке|Местоположение ошибки|  
|-------------------|--------------------|  
|(Microsoft) (менеджер драйвера ODBC) *сообщение-текст*|Менеджер драйвера (Odbc32.dll)|  
|(Microsoft) «Имя *водителя*ODBC» *сообщение-текст*|Водитель ISAM (см. Водитель ISAMs)|
