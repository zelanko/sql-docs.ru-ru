---
title: "Сообщения об ошибках Jet ODBC | Документы Microsoft"
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
helpviewer_keywords: error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 206ebbdc1dd8a121f3c41f95cd305de6f4ef3d10
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-jet-error-messages"></a>ODBC Jet сообщения об ошибках
Для ошибок, возникающих в источнике данных драйвер ODBC возвращает сообщение об ошибке, возвращенные библиотека файлов ODBC. Для ошибок, возникших в драйвере ODBC или диспетчера драйверов драйвер возвращает сообщение об ошибке на основе текста, связанное с SQLSTATE.  
  
 Сообщения об ошибках имеют следующий формат:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Префиксы в квадратные скобки ([]) определения местоположения ошибки. При возникновении ошибки в диспетчер драйверов *источника данных* не предоставляется. При возникновении ошибки в источнике данных [*поставщика*] и [*компонентов ODBC*] префиксы определения поставщика и имя компонента ODBC, который получил ошибку от источника данных.  
  
 В следующей таблице приведены сообщения об ошибках, возвращаемых диспетчером драйверов и драйверов ISAM:  
  
|Сообщение об ошибке|Расположение ошибок|  
|-------------------|--------------------|  
|[Microsoft] [Диспетчер драйверов ODBC] *текст сообщения*|Диспетчер драйверов (Odbc32.dll)|  
|[Microsoft] [ODBC *имя драйвера*]*текст сообщения*|Драйвер ISAM (см. ISAMs драйверов)|
