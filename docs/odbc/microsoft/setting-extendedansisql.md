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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b5c2e4ed4d8bd64d02fb6a62861db832f6b0898
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300804"
---
# <a name="setting-extendedansisql"></a>Настройка ExtendedAnsiSQL
Атрибутом можно управлять в строке подключения, добавив атрибут ExtendedAnsiSQL:  
  
|Значение|Описание|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (по умолчанию)|Этот параметр не включает новые функции.|  
|ExtendedAnsiSQL = 1|Этот параметр включает новые функции.|  
  
 Атрибут также можно задать в имени DSN в диалоговом окне **Дополнительные параметры** при настройке имени DSN с помощью панели управления.  
  
 Если задать для атрибута значение 0, новые возможности отключаются. Установка значения 1 включает новые функции.  
  
 Атрибут также можно задать с помощью SQLSetConnectAttr (). Значение атрибута равно 65501 и устанавливается в SQLINTEGER значение 1 или 0, как описано в предыдущей таблице. Его можно вызвать до или после соединения, но лучше вызывать его после подключения из-за порядка, в котором драйвер обрабатывает кэшированные атрибуты соединения и строки подключения.
