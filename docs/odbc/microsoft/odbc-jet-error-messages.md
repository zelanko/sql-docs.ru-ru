---
description: Сообщения об ошибках ODBC Jet
title: Сообщения об ошибках ODBC Jet | Документация Майкрософт
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
ms.openlocfilehash: 19f7d4b00c9e6b206ecd563083c0fcf16ced55e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340720"
---
# <a name="odbc-jet-error-messages"></a>Сообщения об ошибках ODBC Jet
Для ошибок, возникающих в источнике данных, драйвер ODBC возвращает сообщение об ошибке, возвращаемое библиотекой файлов ODBC. Для ошибок, возникающих в драйвере ODBC или диспетчере драйверов, драйвер возвращает сообщение об ошибке, основанное на тексте, связанном с SQLSTATE.  
  
 Сообщения об ошибках имеют следующий формат:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Префиксы в квадратных скобках ([]) указывают расположение ошибки. При возникновении ошибки в диспетчере драйверов *источник данных* не предоставляется. При возникновении ошибки в источнике данных префиксы [*Vendor*] и [*ODBC-Component*] указывают поставщика и имя компонента ODBC, который получил ошибку от источника данных.  
  
 В следующей таблице показаны сообщения об ошибках, возвращенные диспетчером драйверов и драйвером ISAM:  
  
|Сообщение об ошибке|Расположение ошибки|  
|-------------------|--------------------|  
|NNTP [Диспетчер драйверов ODBC] *текст сообщения*|Диспетчер драйверов (Odbc32.dll)|  
|NNTP [ODBC *Driver-Name*] *текст сообщения*|Драйвер ISAM (см. драйвер ISAM)|
