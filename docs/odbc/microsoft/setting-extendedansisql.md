---
title: Настройка ExtendedAnsiSQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9b8999e229e8a6ed4804b2f06a4072d139ae93a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63159366"
---
# <a name="setting-extendedansisql"></a>Настройка ExtendedAnsiSQL
Атрибут можно контролировать в строке подключения, добавив атрибут ExtendedAnsiSQL:  
  
|Значение|Описание|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (по умолчанию)|Этот параметр не поддерживает новые функции.|  
|ExtendedAnsiSQL = 1|Этот параметр включает новые функции.|  
  
 Атрибут можно также задать в DSN через **Дополнительно** диалоговое окно при настройке имени DSN через панель управления.  
  
 Задать для атрибута значение 0 отключает новые функции; Установите значение 1 включает новые функции.  
  
 Атрибут можно также задать с помощью SQLSetConnectAttr(). Значение атрибута является 65501 и имеет значение SQLINTEGER значение 1 или 0, как описано в предыдущей таблице. Может быть вызвана до или после подключения, но лучше вызывать его после подключения из-за порядка, в котором кэшируются процессы драйвера атрибуты соединения и строки подключения.
