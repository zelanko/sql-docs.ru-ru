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
manager: craigg
ms.openlocfilehash: ec549f256caeab598f6e49632b2a50cfa5841710
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620282"
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
