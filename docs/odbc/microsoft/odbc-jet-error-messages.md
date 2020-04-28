---
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
ms.openlocfilehash: e8fa6e672b69c7791e66dc3919e6fcd22b7c3de7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81293114"
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
|NNTP [Диспетчер драйверов ODBC] *текст сообщения*|Диспетчер драйверов (библиотеками odbc32. dll)|  
|NNTP [ODBC *Driver-Name*] *текст сообщения*|Драйвер ISAM (см. драйвер ISAM)|
