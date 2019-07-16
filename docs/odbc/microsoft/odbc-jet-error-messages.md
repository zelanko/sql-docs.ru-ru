---
title: ODBC Jet сообщения об ошибках | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85e0f9a8bc7015a0ad5b12ce46a6c94ab31ca43c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915817"
---
# <a name="odbc-jet-error-messages"></a>Сообщения об ошибках ODBC Jet
Для ошибок, возникших в источнике данных драйвер ODBC возвращает сообщение об ошибке, возвращаемый библиотеке файлов ODBC. Для ошибок, возникших в драйвере ODBC или диспетчера драйверов этот драйвер возвращает сообщение об ошибке на основе текста, связанный с SQLSTATE.  
  
 Сообщения об ошибках имеют следующий формат:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Префиксы в квадратные скобки ([]) Определите расположение ошибки. При возникновении ошибки в диспетчер драйверов *источника данных* не имеет. При возникновении ошибки в источнике данных [*поставщика*] и [*ODBC-компонент*] префиксы определения поставщика и имя компонента ODBC, который сообщение об ошибке из источника данных.  
  
 В следующей таблице показаны сообщения об ошибках, диспетчер драйверов и драйверов ISAM:  
  
|Сообщение об ошибке|Расположение ошибки|  
|-------------------|--------------------|  
|[Майкрософт] [Диспетчер драйверов ODBC] *текст сообщения*|Диспетчер драйверов (Odbc32.dll)|  
|[Майкрософт] [ODBC *имя драйвера*]*текст сообщения*|Драйвер ISAM (см. в разделе ISAMs драйвера)|
