---
title: Параметр ExtendedAnsiSQL | Документы Microsoft
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
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d36c9462f2525930d8f3943461593bc3f51a95e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setting-extendedansisql"></a>Параметр ExtendedAnsiSQL
Атрибут можно управлять в строке подключения, добавив атрибут ExtendedAnsiSQL:  
  
|Значение|Описание|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (по умолчанию)|Этот параметр не включает новые функции.|  
|ExtendedAnsiSQL = 1|Этот параметр включает новые функции.|  
  
 Атрибут можно также задать в DSN через **Дополнительно** диалоговое окно при настройке DSN через панель управления.  
  
 Задать для атрибута значение 0 отключает новые функции; Установите значение 1 включает новые функции.  
  
 Атрибут можно также задать с помощью SQLSetConnectAttr(). Значение атрибута является 65501 и имеет значение SQLINTEGER значение 1 или 0, как описано в предыдущей таблице. Он может быть вызван до или после соединения, но лучше будет вызывать его после подключения из-за порядок кэширования процессы драйвера, атрибуты соединения и строки подключения.
